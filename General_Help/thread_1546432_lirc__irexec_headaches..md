---
title: "lirc / irexec headaches."
date: 2010-08-05
forum: General Help
---

### Post by teek5449 on 2010-08-05
So I am to the point of where I am ready to give up and am hoping for some insight. Yup, I have tried searching and searching with no real help.

So, my problem: Lirc and irexex startup issues. As it stands now Lirc will start pretty much on its own (not every time though) but I have yet to get irexec to startup successfully by itself. 

Even if I run```
sudo service lirc restart
```irexec will not start even though it says that the deamon has started successfully. If I run```
sudo service lirc restart
sudo irexec -d
```everything works great and the remote works as intended. Running as non root the remote will not work. This tells me that the configurations are correct and that there is a problem when lirc is started.

This is for my HTPC machine and I have it set to automatically log in. << Thinking that this might be part of the problem. It just bugs me that I can get it to work via the terminal manually but I can just not get it to start automatically.

I have tried soooo many "solutions" that I am at a loss now. If anyone can help me with this issue that would be great. Even point me to where I can look for log files that might help me debug this problem. Even a startup script that would work. I have tried a few different approaches with no joy.

Looking for a fresh set of eyes on this one. [-o<

---

### Post by NT4usB on 2010-08-05
Way back when, I ran into this, setting up MythTV on Dapper. I futzed around with permissions on lirc things until I got it working. Don't ask me what files... that was a long time ago, and crs has set in.
What HTPC software you using? Mythbuntu has a sweet utility that automagically configures lirc. Probably only good for MythTV though...

---

### Post by teek5449 on 2010-08-07
Well, lirc and irexec work great if I manually start them via the terminal. The configuration is fine as far as once lirc is started everything works as intended. 

I am sure that this 'is' a permissions issue but I am just not sure where to focus on. I have tried adding both lirc and irexec separately to the startup list with no joy. 

Just want a simple program to run on boot but it will just not work.

---

