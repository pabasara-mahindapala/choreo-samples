# JMS Message Store Sample - Micro Integrator

This sample demonstrates how to deploy a Micro Integrator component in Choreo that use JMS Message Stores and Message Processors.

## Prerequisites
- Running ActiveMQ broker in your local machine.
- Expose the ActiveMQ broker to the internet using ngrok. You can use the following command to expose the ActiveMQ broker.
    ```shell
    ngrok tcp 10088
    ```

## Deploying the component in Choreo
1. Fork this repository.
2. Create an `Service` component in Choreo.
    - Log in to Choreo and click on the `Create Component` button.
    - Select the `Service` component type.
    - Select the `WSO2 Micro Integrator` build pack.
    - Select the `mi-jms-message-store` directory as the project directory.
    - Click on the `Create` button.
3. Building and deploying the component
    - Build the component.
    - Before deploying the component, add the below environment variable.
        - `JMS_URL` for `Name` and the ActiveMQ TCP URL you have exposed for `Value` (eg: `tcp://0.tcp.ap.ngrok.io:10088`)
    - Deploy the component.

## Testing the component

1. Go to the Test Console of your component and send a POST request to the `/jms/test` endpoint with a sample payload.
    ```json
    {
        "paymentId": "1234",
        "amount": 100.0,
        "currency": "USD"
    }
    ```
    This will store the message in the JMS Message Store. It will be processed by the Message Processor and sent to a sequence for logging.
2. You can observe the logs of the component to see the message received by the component.

