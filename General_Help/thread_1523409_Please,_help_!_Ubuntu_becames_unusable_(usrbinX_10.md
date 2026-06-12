---
title: "Please, help ! Ubuntu becames unusable (/usr/bin/X 100% CPU)"
date: 2010-07-03
forum: General Help
---

### Post by vur246 on 2010-07-03
Please, help !

In last month or so Ubuntu 10.04 becomes absolutely unusable !
Each time computer/screen returns from sleep, it freezes (except from mouse). ssh from other computer shows that /usr/bin/X consumes 100% CPU.

The only things to do is to Ctrl-Alt-Backspace to log out and then login again (until next freeze) or to kill this X process from SSH session( that causes log out as well) 

Any advices ?

---

### Post by sanderd17 on 2010-07-03
My advise: unless you trust the persons from this forum completely. Don't try to solve it. This is one of those bugs. If you try to fix them, you're more likely to break your whole OS than fixing anything.

Off course, If you don't mind breaking your OS. You can try suggested solutions for future reference.

PS. I had this kind of thing in ubuntu 8.10 or 8.04 (don't remeber exactly) but it was solved with the next release.

---

### Post by Lolpanda on 2010-07-03
No idea if this will work, but if it's enabled, under screensaver, disable "lock screen when screensaver is active" and then do alt-F2, I think it's "Apps > gnome-power-management" not sure what sub category after that but look for "Can_Hibernate" and "Can_Suspend" or something close to that. Disable them both unless you need them. See if that fixes it, doubtful but possibly

---

### Post by ajgreeny on 2010-07-03
Instead of **Ctrl+Alt+Backspace** try **Ctrl+Alt+F1** and then login and run ```
top
``` to see what is using all your cpu.

Ctrl+Alt+F1 will not shutdown the GUI desktop, but just take you to a command line from where the top command will show all the processes running with highest cpu usage at the top of the list.  Once you know what is eating up your cpu, it may be possible to stop it doing so in future.

---

### Post by vur246 on 2010-07-03
ajgreeny, I know exactly what is consuming my CPU . It's /usr/bin/X 

despite being frozen I can ssh from other computer to my desktop and see the processes by using "top".

When I kill this /usr/bin/X from ssh session it causes the desktop to log out.

So it's not a problem that I don't know what is consuming 100% CPU.

I did a search and looks like multiple people have issue with it but nobody comes with definite solution

---

### Post by ajgreeny on 2010-07-04
OK, sorry, I didn't notice that in your opening post.

---

### Post by jwbrase on 2010-07-04
Machine specs? Are you using an ATI card?

---

### Post by vur246 on 2010-07-04
I am using Nvidia GeForce 7900 GS

Processor

Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz

The bad news is that from today morning I can't even see the gnome desktop.
After I reboot I get a black screen. When I ssh from my laptop I see
that /usr/bin/X get 100% CPU .

I tried to reinstall nvidia drivers, didn't help. I can log-in in low graphic mode. I installed the previous version of nvidia drivers didn't help either. 

So now I can't use ubuntu at all !

I did a search on the internet and it's full of description of this problem requests to escalate etc it but nowhere there is a solution

---

### Post by vur246 on 2010-07-05
Yesterday I've did a full reinstall from CD of 10.04 32 bit. Almost immediately the /usr/bin/X problem appeared again. I removed the nvidia-current version of drivers and installed nvidia-173. After it the problems disappeared. 

I am not sure if it's nvidia problem , xorg problem or both. There is no way to know who bombards xorg with numerious requests so it causes it to grab 100% CPU.

---

### Post by Slug71 on 2010-07-05
Personally i think the culprit is Update Manager.

---

