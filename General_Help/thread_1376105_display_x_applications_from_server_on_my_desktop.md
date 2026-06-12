---
title: "display x applications from server on my desktop"
date: 2010-01-08
forum: General Help
---

### Post by knipknup on 2010-01-08
Hi,

I have a karmic server and a separate karmic desktop (laptop).

I want to run a few gui applications from the server to my desktop so they will be centralized.

I can successfully ssh to my server from the laptop, but getting the gui stuff launched from the server to display on my laptop is where I am hitting a wall.

I did:
$ ssh -Y knipknup@192.168.1.3
enter password

and I get:
/usr/bin/X11/xauth:  error in locking authority file /home/knipknup/.Xauthority

I also did (which may not be a good idea?):
$ sudo chmod -v 777 /home/knipknup/.Xauthority

and that results in the same message.

Thanks for help.

---

### Post by knipknup on 2010-01-08
Well, I found that if I do:
ssh -Y 192.168.1.3

It works.

I only have one user on each box named knipknup.  However, these are probably not 'thought' of as the same user by both boxes.  Maybe that is my problem.

What is the best solution to have my single user recognized on both the client and server?

Sorry, I am a recovering M$aholic...

---

