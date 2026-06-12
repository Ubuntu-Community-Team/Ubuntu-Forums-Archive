---
title: "Mount SSH Tunnel in Ubuntu"
date: 2010-10-04
forum: General Help
---

### Post by dyous87 on 2010-10-04
I have an Ubuntu Server in my office that I can ssh into remotely using a tunnel.

For example lets say my office server is ServerA. To access ServerA remotely I can first ssh into another sever (ServerB) and then from ServerB run the command:

```
ssh user@localhost -p 50022
```

to ssh into ServerA.

In windows I figured out how to use WinSCP to allow people in my office to be able to remotely browse the files on ServerA with a GUI.

In Ubuntu I can obviously connect to a server from Places>Connect to server, but this only allows me to make a regular SSH/SFTP connection and there is no option of connecting to a tunnel. 

Is there anyway in ubuntu to be able to mount of browse files over an SSH tunnel?

I've tried using sshfs by the way but I can't figure out if there is a way to mount a connection over an ssh tunnel with sshfs.

Thanks is advance for your help.

---

