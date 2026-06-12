---
title: "SSH + Display question"
date: 2012-01-01
forum: General Help
---

### Post by Colo2 on 2012-01-01
Hey

I have a desktop PC running Ubuntu with Gnome GUI, and a windows laptop. 

I want to be able to connect to the desktop with SSH, and command GUI applications to launch.

Example, from PuTTy, running the command: "firefox".

Thing is, SSH wont let me run applications needing an X environment, or something?

My question, is there a way to run SSH commands to start up GUI applications? maybe by specifiying a display or something?

Thanks

Tom

---

### Post by Lampi on 2012-01-01
connect to your ssh server with X forwarding

from the man page:
```

 -X      Enables X11 forwarding.  This can also be specified on a per-host basis in a configuration file.
```

---

### Post by Colo2 on 2012-01-01
Hey

Thanks for the reply. 

> Error: cannot open display: localhost:10.0

I'm using plink.exe, AKA, 1 time command execution:

> "C:\plink.exe" USER@HOST -X -pw PASSWORD COMMAND

Thanks

Tom

---

### Post by Colo2 on 2012-01-01
No ideas?

---

### Post by Synoc on 2012-01-01
[URL="http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html"]http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html
[/URL]
don't know if this link is what you are looking for.

---

### Post by Colo2 on 2012-01-01
Hey

I dont have an Xconfig file, or an /etc/X11/xorg.conf file

Confused.. :S

Tom

---

### Post by rsvancara on 2012-01-01
You could install something like xming and putty, enable X11 forwarding in Putty.  And then to make commands start automatically upon login, like firefox, you could add the following like to your ~/.bash_profile

/usr/bin/firefox

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by Colo2 on 2012-01-02
Hey

Thanks for the reply.

It's getting closer to what I need. I tried what you suggested, but the media I try running appears on my local machine. If I launch a movie with command line, totem appears on my Windows laptop playing the movie, on the desktop PC, theres audio only and no sign of totem.

In a perfect world, I dont want anything coming up on the Windows laptop, and for it to launch on the desktop. AKA, this will act as a remote control for media on my desktop PC

Thanks

Tom

---

### Post by Dangertux on 2012-01-02
> **Colo2 said:**
> Hey

Thanks for the reply.

It's getting closer to what I need. I tried what you suggested, but the media I try running appears on my local machine. If I launch a movie with command line, totem appears on my Windows laptop playing the movie, on the desktop PC, theres audio only and no sign of totem.

In a perfect world, I dont want anything coming up on the Windows laptop, and for it to launch on the desktop. AKA, this will act as a remote control for media on my desktop PC

Thanks

Tom

Then you need to not be using X Forwarding over SSH. The reason this is happening is X Forwarding runs the application locally. 

Meaning if I run firefox over SSH X Forwarding then it's running on my local machine. If that makes sense.

---

### Post by spiky001 on 2012-01-02
How about a vnc client that connects to vnc server you can close the vnc viewer when what ever you want to run then open vnc viewer

---

### Post by Colo2 on 2012-01-02
> **Dangertux said:**
> Then you need to not be using X Forwarding over SSH. The reason this is happening is X Forwarding runs the application locally. 

Meaning if I run firefox over SSH X Forwarding then it's running on my local machine. If that makes sense.

Hey ,

Yeah, I realize that now. Is there a way to do what I need to do?

Tom


> How about a vnc client that connects to vnc server you can close the vnc viewer when what ever you want to run then open vnc viewer

I thought about VNC, but its not really what I need. I need a command based application, because I'm programming a remote which connects to an SSH server to make commands. But thank you :)

Tom

---

### Post by Colo2 on 2012-01-02
hmm :confused:

---

### Post by efflandt on 2012-01-02
Assuming that X on ssh destination PC is running as you, from the ssh session simply do:

```
export DISPLAY=:0.0
```(those are zeros)

Then whatever X program you run from ssh will run and display on the sshd PC.

---

### Post by Colo2 on 2012-01-02
You have no idea how happy I am haha :P I've been scrolling through X documentation to try and find the answer to this!

Thanks man :) works brilliantly.

---

