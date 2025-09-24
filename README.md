# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.

# Chat Server
## PROGRAM
```
import socket

def chat_server(host='127.0.0.1', port=65432):
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)
    print(f"Chat Server started on {host}:{port}")

    conn, addr = server_socket.accept()
    print("Connected with:", addr)

    while True:
        data = conn.recv(1024).decode()
        if not data or data.lower() == "exit":
            print("Client disconnected.")
            break
        print("Client:", data)
        message = input("You: ")
        conn.sendall(message.encode())
        if message.lower() == "exit":
            break

    conn.close()
    server_socket.close()

if __name__ == "__main__":
    chat_server()
```
## OUPUT

<img width="515" height="174" alt="Screenshot 2025-09-24 111558" src="https://github.com/user-attachments/assets/9fd7c0e9-757f-49c3-b95d-5879aed4b506" />

# Chat Client
## PROGRAM
```
import socket

def chat_client(host='127.0.0.1', port=65432):
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))
    print("Connected to Chat Server. Type 'exit' to quit.")

    while True:
        message = input("You: ")
        client_socket.sendall(message.encode())
        if message.lower() == "exit":
            break
        data = client_socket.recv(1024).decode()
        if not data or data.lower() == "exit":
            print("Server disconnected.")
            break
        print("Server:", data)

    client_socket.close()

if __name__ == "__main__":
    chat_client()
```
## OUTPUT

<img width="577" height="200" alt="Screenshot 2025-09-24 111551" src="https://github.com/user-attachments/assets/d0e652ae-9b7c-4b5e-91a8-76299af57240" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
