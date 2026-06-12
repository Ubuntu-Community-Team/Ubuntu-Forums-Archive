---
title: "Terminal instead of desktop"
date: 2010-05-20
forum: General Help
---

### Post by Zanven on 2010-05-20
Well Lucid Lynx worked fine on my laptop for some time now and so I decided to switch on my desktop. I upgraded using Update Manager and I had the (now after searching infamous) hang up getting stuck with 13 minutes to go.

I don't know if I was in a hurry, panicked or angry but I rebooted like an idiot and I had a grub problem which I fixed using the forums but now it boots and asks me in command line my login and password and logs into a terminal. "ls -l" returns the contents of my home folder so I'm in but only in a terminal. Help?

---

### Post by john newbuntu on 2010-05-20
please ignore I was responding to the wrong thread.

---

### Post by john newbuntu on 2010-05-20
Please check the following log files for any errors
with the following command - one at a time (Hit space bar to scroll down.  When done, hit q):
less /var/log/user.log
less /var/log/Xorg.0.log
less /var/log/messages
less /var/log/syslog

You might also want to try:
sudo apt-get update[I]
sudo dpkg --configure -a 

[/I]

---

### Post by lukeiamyourfather on 2010-05-20
If you run "startx" does it do anything?

---

### Post by Zanven on 2010-05-20
Ok so an update for my situation is after getting back from work and its been off all day it now did boot to low graphics mode and so I went to the reconfigure graphics option and made a new config file I believe. And it restart and now my monitor is not recieving any signal. This happens everytime I boot normally now.
I can still get to low graphics mode by booting in recovery mode and choosing "boot in xfalesafe mode" or something similar.

I don't know why leaving it off all day changed its behavior but now in this state what of the above is should I still try and what should I do now? Thanks in advanced for helping me out.

---

### Post by Serpher on 2010-05-20
> **lukeiamyourfather said:**
> If you run "startx" does it do anything?

startx isn't in Ubuntu or any Debian based Linux to my knowledge. Use:

```
sudo /etc/init.d/gdm start
```

---

### Post by amac777 on 2010-05-20
I'm having similar problems of getting a console instead of GDM but I think it's due to nvidia issues. Anyway, for me I login at the console and then run this command:

```
sudo service gdm start
```

That starts up gdm fine and everything is great until I reboot the computer again.

---

### Post by Nythain on 2010-05-20
> **Serpher said:**
> startx isn't in Ubuntu or any Debian based Linux to my knowledge. Use:

```
sudo /etc/init.d/gdm start
```

startx is most certainly in ubuntu, its what i use to well, start x :P
its just not the standard default way to get a display manager going but its worth a shot if the display manager itself doesnt work, to at least see if X is working

---

### Post by Zanven on 2010-05-27
I just backed up my stuff and re-installed karmic. Problem solved

---

