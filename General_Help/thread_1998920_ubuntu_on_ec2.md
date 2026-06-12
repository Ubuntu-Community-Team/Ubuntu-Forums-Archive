---
title: "ubuntu on ec2"
date: 2012-06-07
forum: General Help
---

### Post by kgilmore on 2012-06-07
Hi,

I've been using ec2 to host ubuntu servers, but have a small problem.

Everytime I restart an instance I must do the following two tasks in order to connect to them.

1. putty (telnet) to the server and start vnc by using
```
vncserver :0
```

2. vnc to the server and type in the following command which starts the GUI
```
nohup gnome-session&
```

I've tried adding them to the startup file rc.local i think, but it didn't work. I want to just be able to restart the server and vnc straight into the giu without having to do those two commands.

Thanks.

---

