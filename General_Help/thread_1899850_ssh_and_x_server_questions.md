---
title: "ssh and x server questions"
date: 2011-12-24
forum: General Help
---

### Post by zero2xiii on 2011-12-24
Hay all,

Fist happy holidays to all and a merry xmas to all. Hope everything is happy and joyful for you in this season :)


Now down to the stuff haha... So I read this article:
[http://polishlinux.org/apps/ssh-tricks/](http://polishlinux.org/apps/ssh-tricks/)

seeing that **ssh -X [email]user@xxx.xxx.xxx.xxx[/email]** allows me to run applications on the remote machine, while having the window displayed localy. This is EXACTLY what I wanted to do on an earlier stage, but resorted to insane other measures to get it going. 

However, I am now curious if this can be modified to display (even if no interaction is possible) an already open screen of the remote machine.

The Idea is simple:
I have a Gigabit network setup on my home networkm all running Ubuntu (or variants) and would like to stream a single video file for example to all of them. Or just see what the kids are up to on the computers.

I wonder if the PID will be helpful doing the ssh -X as above mentioned, then running let say **ps -e** and then see, ah opera is running (the web browser) and then "tunnel" the window to my x server, just as it would have done if I ran "opera" in the open terminal and have the opera window displayed localy.

This will also help me A LOT with some of the servers I run that does not have sceens attached to them, which executes sripts that generate output.

If it is possible to interact it will be a bonus, but this will purely be a luxury. Thanks a lot in advance!
Cherz

---

### Post by zero2xiii on 2011-12-24
One thing I forgot.

Some of the ubuntu PCs is to old to install apps on, for example the "family computer" still runs ubuntu 9.04, and since it gives no problems, and its almost full... I cant (and dont really want to) upgrade it to a later, supported version.

SO I cant install for example xvnc or vncviewer on it. Since the repro's are dead.

But ssh - X works

Cherz

---

### Post by btindie on 2011-12-24
I haven't heard of the feature you describe, but there are some other things that may fit your requirements.

When using X-Forwarding it's best to use -Y instead of -X, see "man ssh".

There's a few terminal multiplexers available, tmux / screen, that  allows you to run applications in a SSH session, disconnect and later  reconnect and resume from where you left off. It's handy for working on  remote servers when your connection could die.

To access the remote 'desktop' you can use VNC which allow you to  connect to the current session remotely. It can work in either read-only  mode or interactively. There's also a package called [x2go]("http://www.x2go.org/wiki:x2go-repository-ubuntu") which is similar put performs better and requires more configuration.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by zero2xiii on 2011-12-25
Hay,

Thanks. Seeing as there seems to be no solution for what I am asking I will mark this thread as solved.

I use "screen" on the most servers with great success. But I was looking for something that can be used similarly but with x11 support. I will look into the other options listed, but seeing as I can not install on some systems, this will only be a solution for the rest.

But thank you non the less :)
Xmas greetings

---

### Post by Lars Noodén on 2011-12-25
You could try tunneling [VNC over SSH](https://help.ubuntu.com/community/VNC).  It's insecure by itself, still.  That will give you a view of existing windows.

---

### Post by Synoc on 2011-12-25
+1 for VNC, however, opening a virtual desktop, everytime I've tried it has been nightmarishly slow. and half the time inputting passwords has not worked as a result. perhaps it's the old PC I was remoting into that was the problem. However, it is something to keep in mind.

---

### Post by Lampi on 2011-12-25
xwud could capture a screenshot of your remote desktop, then  transfer it to your local station,  convert to sth small ... that should be ready to use on your jaunty install.

---

### Post by zero2xiii on 2011-12-26
Hay,

Thanks I have found the following that seems to do the trick on the older machines:

```
xwd -out screenshot.xwd -root -display :0.0
```

I could not get the syntax for xwud right to get it working. But the above works non the less, using xwud to view the file or just open the image viewer on it is fine since I am using **ssh -Y** it seems to work.

Thanks for all the help people :)
Cherz

---

