---
title: "How to access desktop remotely?"
date: 2012-07-27
forum: General Help
---

### Post by foxy123 on 2012-07-27
I need to access a remote PC in graphic mode. It runs on Ubuntu 11.10 and the local laptop runs on 12.04. I know how to run certain programmes in graphic mode (with -X or -Y) but I need to get into Unity desktop on the remote laptop. I tried to set up vino but vino-preferences does not run in graphic mode remotely. x11vnc does not work for me either (I do not know how to set up it). Any suggestions will be really appreciated.

---

### Post by steeldriver on 2012-07-27
Here are instructions for starting x11vnc via command line that I posted earlier

[http://ubuntuforums.org/showpost.php?p=12133116&postcount=4](http://ubuntuforums.org/showpost.php?p=12133116&postcount=4)

---

### Post by foxy123 on 2012-07-27
> **steeldriver said:**
> Here are instructions for starting x11vnc via command line that I posted earlier

[http://ubuntuforums.org/showpost.php?p=12133116&postcount=4](http://ubuntuforums.org/showpost.php?p=12133116&postcount=4)

Thanks. Should the command be executed on the remote PC? What about vncpasswd?

---

### Post by steeldriver on 2012-07-27
yes on the remote machine - run vncpasswd (one time - follow the instructions) and then start the x11vnc server

you can do everything via ssh if you do not have physical access to the remote machine

---

### Post by foxy123 on 2012-07-27
> **steeldriver said:**
> yes on the remote machine - run vncpasswd (one time - follow the instructions) and then start the x11vnc server

you can do everything via ssh if you do not have physical access to the remote machine

do I have to install something for vncpasswd?

---

### Post by foxy123 on 2012-07-27
```
:~$ vncpasswd
The program 'vncpasswd' can be found in the following packages:
 * tightvncserver
 * vnc4server
Ask your administrator to install one of them

```

---

### Post by steeldriver on 2012-07-27
try 

```
x11vnc -storepasswd
```

---

### Post by foxy123 on 2012-07-27
> **steeldriver said:**
> try 

```
x11vnc -storepasswd
```

Thanks a lot. What VNC client would you recommend. I have Remmina installed but it's got a lot of settings I do not know (like Repeater)?

---

### Post by foxy123 on 2012-07-27
got this 
```
X11 MIT Shared Memory Attach failed:
  Is your DISPLAY=localhost:12.0 on a remote machine?
  Note:   DISPLAY=localhost:N suggests a SSH X11 redir to a remote machine.
  Suggestion, use: x11vnc -display :0 ... for local display :0

caught X11 error:
27/07/2012 18:43:54 deleted 43 tile_row polling images.
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  140 (MIT-SHM)
  Minor opcode of failed request:  1 (X_ShmAttach)
  Serial number of failed request:  48
  Current serial number in output stream:  93

```

---

### Post by foxy123 on 2012-07-29
I have managed to connect using a different method from [**here**]("http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_11.04_Unity_Desktop"), by establishing a SSH tunnel:
```
ssh -L 5900:localhost:5900 hostname
``` and connecting through it:
```
vncviewer localhost::5900
``` or ```
vinagre localhost:5900
``` and it works very well for me.

I have noticed that in Reminna there is an option to establish SSH tunnel together with VNC so it would be much easier to connect but I cannot configure it. Tried to use a guide from [**here**]("http://community.linuxmint.com/tutorial/view/83") but it does not work for me.

---

