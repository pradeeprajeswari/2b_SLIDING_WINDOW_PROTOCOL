# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
Client
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send :"))
l=list(range(size))
s=int(input("Enter Window Size:"))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s

Server
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgment recived from the server".encode())
```
## OUPUT

Client
![Screenshot 2024-09-14 132059](https://github.com/user-attachments/assets/5aa8881f-2707-4485-b9fb-0410e335c232)

Server
![Screenshot 2024-09-14 132107](https://github.com/user-attachments/assets/206f20dd-6945-49db-baf4-b1090aeed5f3)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
