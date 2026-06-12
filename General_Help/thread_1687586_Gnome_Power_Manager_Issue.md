---
title: "Gnome Power Manager Issue"
date: 2011-02-14
forum: General Help
---

### Post by St Nabi on 2011-02-14
Hi people, 

I tried to open my computer last night and again this morning but I am getting the following message :-

"Install Problem
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator."

A slightly different log-on screen appears but when entering the password for any of the users, it just goes back to the same log-on screen.

I have not changed or added anything new and am not trying to open the computer in any different way.

I just do not understand what has happened.

Any help would be very welcome.

Thanks in advance !!!

---

### Post by Wtower on 2011-02-14
This has happened to me once on a small office server running Ubuntu desktop. I didn't quite understand what exactly caused it, but it had happened as a result of the disk space running suddenly low (another reason why disk partitioning is very important at the first place).

Also, unfortunately I do not remember how exactly I solved it, so we will have to work it out. I cannot guarantee that this will safely work but it did for me.

How is your disk status? Can you open up a terminal session (xterm, ssh, whatever)? In terminal, try:

```
sudo apt-get purge gnome-power-manager gnome-applets
sudo apt-get install gnome-power-manager gnome-applets
sudo reboot now
```

---

### Post by St Nabi on 2011-02-14
I thought it might have been the cause. How can I increase the disk space? 
What happens if I can't access the system ? In other words, I need to be able to get into Ubuntu, as far as I am aware, before I can open a terminal session, right ?

Nonetheless, I will try to open a terminal session from somewhere.

Will update you shortly.

I am glad that I am not the only person that this has happened to !!!

---

### Post by St Nabi on 2011-02-15
You know what I did was install another copy of Ubuntu with a greater disk space allocated to it next to the existing Ubuntu. From there I went and deleted some files and hey presto. Everything is back to normal again !
So the old version will now act as a back up Ubuntu and the new one is the one I will be using from now on. It's great because if for whatever reason one corrupts, then I can use the other one to get back into it!
Issue resolved nonetheless !

---

### Post by Wtower on 2011-02-16
Nice, I'm quite glad. Please don't forget to mark the thread as solved using the thread tools.

---

