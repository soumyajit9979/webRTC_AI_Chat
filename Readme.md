# WebRTC AI Chat Demo

Welcome to the **WebRTC AI Chat Demo**! This project demonstrates how WebRTC can be used for real-time audio transmission and data channel communication between browsers, along with integration with OpenAI APIs for enhanced functionality.

---

## 1. What is WebRTC?

WebRTC (Web Real-Time Communication) is a technology that enables real-time communication between browsers without requiring a traditional server intermediary. It supports audio, video, and data transmission, making it ideal for building interactive web applications.

### Key Features of WebRTC:

#### 1.1 Audio Stream Transmission
WebRTC allows capturing and transmitting audio streams between browsers in real-time. For example:
- The local browser captures audio input (e.g., from a microphone) using:
    ```javascript
    navigator.mediaDevices.getUserMedia({ audio: true });
    ```
- The captured audio stream is transmitted to the remote browser using:
    ```javascript
    peerConnection.addTransceiver(track);
    ```

This enables seamless audio communication between users.

#### 1.2 Data Channel Communication
WebRTC also supports **Data Channels**, which provide a reliable, low-latency way to exchange data (e.g., text, binary files) between browsers. In this demo:
- JSON-formatted data is exchanged via the `dataChannel`.
- The data channel enables interaction with remote systems, such as:
    - Changing webpage background color.
    - Retrieving HTML content.
    - Executing JavaScript functions.

---

## 2. Features Demonstrated in the Demo

This demo showcases the following functionalities:
- Retrieve and display current HTML element content.
- Change the webpage background color dynamically.
- Modify font color.
- Adjust button size and color.

---

## 3. How It Works: Step-by-Step

### 3.1 Local Browser Initiates Request
The user's browser initiates a WebRTC connection request by sending a request to the backend's `/api/rtc-connect` endpoint. This request includes:
- The local browser's media stream.
- Network settings and other connection details.

### 3.2 Backend Processes the Request
The backend:
1. Processes the connection request.
2. Calls the OpenAI API to generate WebRTC SDP (Session Description Protocol) data, which includes:
     - Audio stream configurations.
     - Data channel settings.
     - Network parameters.

### 3.3 Backend Returns SDP Information
The backend sends the generated SDP data back to the local browser. This data contains all the necessary configurations for establishing a WebRTC connection.

### 3.4 Local Browser Processes SDP Data
The local browser uses the SDP data to establish the WebRTC connection:
- **Audio Stream**: Starts transmitting and receiving audio streams.
- **Data Channel**: Sets up a channel for exchanging messages and commands.
- **ICE Connection**: Performs NAT traversal using `ice-ufrag` and `ice-pwd` to establish a network connection.

### 3.5 WebRTC Connection Established
Once the connection is established, the local browser communicates with the remote device (OpenAI API) via:
- **Audio Stream**: Transmitting real-time audio.
- **Data Channel**: Sending and receiving commands or data.

### 3.6 Remote Device (OpenAI API)
The OpenAI API acts as the remote WebRTC endpoint, performing the following tasks:
- Receiving and processing audio streams.
- Executing commands sent via the data channel.
- Returning processed data or audio feedback to the local browser.

---

## 4. Configuration

To set up the demo, follow these steps:

1. **Backend Configuration**:
     - Set the backend port.
     - Provide your `apiKey` for OpenAI API access.

2. **Frontend Configuration**:
     - Update the frontend to point to the backend's `baseUrl`.

---

## 5. Running the Demo

To run the demo, follow these steps:

1. install libraries:
    ```bach
    pip install -r requirements.txt
    ```

2. Start the backend:
    ```bash
    python WebRTC.py
    ```
3. Open the `index.html` file in a live server to view the demo in action.

---

## 6. Why Use This Demo?

This demo is a practical example of how WebRTC can be combined with AI to create interactive, real-time web applications. It highlights:
- The power of WebRTC for real-time communication.
- The flexibility of Data Channels for exchanging commands and data.
- The potential of integrating AI for enhanced user experiences.

---

Explore the possibilities of WebRTC and AI with this demo. Happy coding!
