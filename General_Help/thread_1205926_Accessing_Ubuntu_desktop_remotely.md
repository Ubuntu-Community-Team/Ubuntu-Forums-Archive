---
title: "Accessing Ubuntu desktop remotely"
date: 2009-07-06
forum: General Help
---

### Post by BaldNomad on 2009-07-06
I am a Linux newbie, having just installed 9.0.4 on a newly built machine intended to be a Linux server for files and other uses in my small home network consisting of both Mac and PC computers.

I want to be able to remotely connect to and control the Ubuntu desktop.  I've already enabled AFP (Netatalk) and I have been able to remotely connect to Ubuntu using the built-in VNC capabilities of Leopard 10.5.

However, I noticed that when I log out of the Ubuntu machine, my Mac no longer shows the remote server in Finder.  I guess it shows up there because of Bonjour (or whatever it's called under Linux). 

Question: is there a way to do this without leaving a session open on the Ubuntu server?  I supposed I could just use terminal, since the machine is primarily a file server...but I'd like the ability to log on to the remote GUI without first having to establish the session...sort of like the way Windows remote desktop works.

How do most people do this?

thanks for any help!

---

### Post by t4thfavor on 2009-07-06
Never had much luck loggin in without a session active. However, I did manage to learn alot about ssh :)

I would recommend leaving someone logged in, and just locking the screen. Its pretty safe. I do however feel your pain though, a RDP like server would be very nice.

You could run a linux vm, and conect using xdmcp. Its a fat protocol, and its not very quick. But it does not need an active session to work properly.

---

### Post by renkinjutsu on 2009-07-06
i assume VNC would only work with a session active, since what it does is forward whatever's on the host's screen to another computer.

What you COULD do is just use ssh. SSH has sftp filesharing and you also have access to the terminal. If that's not good enough, you can enter the -X parameter and it'll forward X windows... so you can run say gedit on the HOST computer, but have the window displayed on your client computer (all this without a session running!) -- that's actually what linux/UNIX was built for anyway.. a decent computer/server that serves/computes for a bunch of other remote crappy terminal computers

---

