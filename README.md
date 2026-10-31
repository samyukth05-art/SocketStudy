# Ex.No:1a  			Study of Socket Programming
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind(("127.0.0.1", 5000))
    s.listen(1)
    print("Server waiting...")

    conn, addr = s.accept()
    print("Connected by:", addr)

    for _ in range(3):   # conversation for 3 messages
        data = conn.recv(1024).decode()
        print("Client says:", data)

        reply = input("Server reply: ")
        conn.send(reply.encode())

    conn.close()
    s.close()
def client():
    time.sleep(1)  

    c = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    c.connect(("127.0.0.1", 5000))

    for _ in range(3):  
        msg = input("Client: ")
        c.send(msg.encode())

        response = c.recv(1024).decode()
        print("Server says:", response)

    c.close()
server_thread = threading.Thread(target=server)
client_thread = threading.Thread(target=client)

server_thread.start()
client_thread.start()

server_thread.join()
client_thread.join()
```
## Output:
<img width="558" height="177" alt="WhatsApp Image 2026-10-31 at 10 23 49 AM" src="https://github.com/user-attachments/assets/60b2cc61-c6c8-492c-b150-7b4631442af5" />


## Result:
Thus the study of Socket Programming Completed Successfully
