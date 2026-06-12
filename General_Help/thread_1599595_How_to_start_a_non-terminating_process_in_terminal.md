---
title: "How to start a non-terminating process in terminal window?"
date: 2010-10-18
forum: General Help
---

### Post by ashokharnal on 2010-10-18
Please let me know as to how start a process in Ubuntu terminal window that is not killed when the terminal window closes.

---

### Post by Yarui on 2010-10-18
A process that runs in the background even after you have closed the terminal window is known as a daemon.  If you want to learn how to do this it would probably be good to read a bit on how daemons work and see if you can figure out how to make the program you are trying to run into a daemon.  Someone here may have a little more detailed info on how to do that, but if not, hopefully that information will be helpful to you.

I have tried to figure out how to do this with several programs in the past with no luck, but I have never really looked very deeply into it so it could actually be really easy.

---

### Post by matsuzine on 2010-10-18
I think the easy way to launch a background process from a terminal is to do this:

nohup command &

---

### Post by Yarui on 2010-10-18
Ah, that's really nice to know.  Do you know if this command actually runs the program as though it is a daemon where you can use the stop command to end the process?  For example could you:
```

nohup ~/myprogram &

```
and then end it with something like
```

~/myprogram stop

```
or would you have to something else to stop the process?

---

### Post by matsuzine on 2010-10-18
You can use the kill command to stop the process.

It's not exactly a daemon, you're just separating the parent ( terminal ) from the child ( task ).  nohup stands for no hang up, normally when you log out of the terminal it kills the child process on exit.

---

### Post by conradin on 2010-10-18
I think nohup is for preventing program hangs, which is nice, but not necisarry for just launching a background process. Anyways, when the process launches, it with tell you the PID
so then you could give the kill command to terminate the process in any number of ways.
so heres my example:
```

$ gedit file &
[1] 2297
$ kill -9 2297

```
 kill -9 is the strongest form of kill, the process will not respawn. There are 64 some types of kill though depending on what you want to do.

---

### Post by oregonbob on 2010-10-18
> **conradin said:**
> I think nohup is for preventing program hangs, which is nice, but not necisarry for just launching a background process. 

If you don't specify nohup the program will automatically be killed when you exit terminal session. If it is a real daemon, it usually has a mode for background and nohup is not required.

---

### Post by Yarui on 2010-10-18
> **conradin said:**
> kill -9 is the strongest form of kill, the process will not respawn. There are 64 some types of kill though depending on what you want to do.
Interesting.  I might have to read up on that a little bit.  This knowledge should be really helpful to me, since I have been having issues with getting a server to run some programs in the background indefinitely via ssh.  Every time I closed the ssh window the processes would stop.

---

### Post by nothingspecial on 2010-10-18
Another option, especially when running stuff through shh is screen.

```
screen
``` to launch it, then press Ctrl A then D. This will detach the session but keep it running.

To reattach the session, type ```
screen -r
```

This is really useful when logging on to your ssh server with different machines. You can start the process, detatch it, fly half way round the world then log back on to see how it`s going.

---

### Post by dcstar on 2010-10-18
> **oregonbob said:**
> If you don't specify nohup the program will automatically be killed when you exit terminal session. If it is a real daemon, it usually has a mode for background and nohup is not required.

Yep "nohup" means "No Hangup" and is specifically there to keep a process running after the terminal session ends.

Those old enough to remember using dial-up connections to mainframes know how necessary something like that was in the days of dodgy modem connections etc.

---

### Post by blueabysm on 2010-10-18
> **ashokharnal said:**
> Please let me know as to how start a process in Ubuntu terminal window that is not killed when the terminal window closes.

Add a '&' after the command.

for example:
```

sudo apt-get install XXXX &

```

---

### Post by ashokharnal on 2010-10-18
Many thanks for the reply. nohup does the job. Thank you once again.

---

