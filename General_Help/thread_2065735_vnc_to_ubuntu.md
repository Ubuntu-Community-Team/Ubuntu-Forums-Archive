---
title: "vnc to ubuntu"
date: 2012-10-02
forum: General Help
---

### Post by kgilmore on 2012-10-02
Hi,

I have a ubuntu vps and every time I want to connect after reboot I have to do the following,

ssh to the server then type,
```
vncserver :0
```

vnc then type this in to start gnome
```
gnome-session
```

I would like to be able to reboot and vnc straight in to the desktop.

Please can someone help.

PS. I tried adding to the rc.local file but with no avail.

Thanks.

---

### Post by lukeiamyourfather on 2012-10-02
Using VNC is not a good way to access remote machines (can be insecure, resource heavy, bandwidth heavy). Using SSH with X tunneling is much easier on resources and secure. It can be done like this.

```
ssh -X user@host
```

Once connected when you run a command with a GUI it will open the GUI on the local machine instead of the remote host (but will still process on the remote host). So you can use commands like firefox, nautilus, gedit, and whatever your other applications are. If you want to run multiple they can be sent to the background by adding a "&" after the command.

---

### Post by eotakos on 2012-10-05
Did the work for me(!)
(and I was searching for remote-desktop servers etc....)

Thank you for your answer

---

