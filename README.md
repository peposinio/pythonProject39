# pythonProject39
import socket
#ip 0.0.0.0
#port 1337
s = socket.socket()
s.bind(("0.0.0.0", 1337))
s.listen()
print("you got listening!!!")

cs, clint_addres = s.accept()
print("connected")
info = cs.recv(2048).decode()
while info != "exit\n":
    try:
        cs.send(info.encode())
        print(info)
        txt = s.recv(2048).decode()
        print(txt)
    except:
        info = "exit"

cs.close()
s.close()
