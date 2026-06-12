---
title: "need help with recovery mode."
date: 2010-03-08
forum: General Help
---

### Post by anklebone12 on 2010-03-08
Hi,

I just installed Ubuntu the other day and everything went without hitch until I started configuring the Compiz plug-ins (3dshell, wobbly windows etc...) and the system froze. Whenever I boot up the computer the system freezes almost immediately. I'm currently using the live cd to search for solution on the internet.

 I believe I need to go into recovery mode but I do not know which option I need to select. dpkg or xfix is what I'm thinking. I just want to get to the earliest working time before I activated the plug-ins. 

Thanks

---

### Post by Sin@Sin-Sacrifice on 2010-03-08
xfix should do it if the problems started happening since compiz was turned on. You could also just go into the root terminal and use ```
metacity --replace
``` so compiz doesn't load. Usually freezing is a sign of hardware failure though so beware. I would do a memtest regardless. Do you get blinking caps lock or does the screen just stop (better yet can you ssh into it from another PC)? Hopefully it is just graphics driver issues.

---

### Post by Techsnap on 2010-03-08
> Usually freezing is a sign of hardware failure though so beware. I would do a memtest regardless.

No, it's more than likely incorrect Video drivers. Don't go and buy new hardware, you don't need it.

---

### Post by anklebone12 on 2010-03-08
> **Sin@Sin-Sacrifice said:**
> xfix should do it if the problems started happening since compiz was turned on. You could also just go into the root terminal and use ```
metacity --replace
``` so compiz doesn't load. Usually freezing is a sign of hardware failure though so beware. I would do a memtest regardless. Do you get blinking caps lock or does the screen just stop (better yet can you ssh into it from another PC)? Hopefully it is just graphics driver issues.

What I think is that it is a hardware compatability problem. 

I'm kind of new to this so some clarification would be nice. to log in to root, I type ```
 su
``` and then I would type ```
metacity --replace
``` in order stop compiz from loading after booting up?  This works from live cd also right?

Thank you so much for responding to me. Your help is immensely appreciated.

---

### Post by kamallneet on 2010-03-08
You need to get to a shell where you can work with the installed system. I guess recovery mode will give you that. If it doesn't, you can just do "sudo chroot /dev/sdan" from live CD (replace sdan with actual partition of the installed system, e.g. sda3).
Then, either you can try the metacity command that someone suggested. Or, just "sudo apt-get purge <compiz-packages>".

---

### Post by anklebone12 on 2010-03-08
> **kamallneet said:**
> You need to get to a shell where you can work with the installed system. I guess recovery mode will give you that. If it doesn't, you can just do "sudo chroot /dev/sdan" from live CD (replace sdan with actual partition of the installed system, e.g. sda3).
Then, either you can try the metacity command that someone suggested. Or, just "sudo apt-get purge <compiz-packages>".

I did this "sudo chroot /dev/sda1". It said "Not a directory".

I went ahead and did the metacity command anyway and the process is still running but there is no output info.

---

### Post by kamallneet on 2010-03-08
> **anklebone12 said:**
> I did this "sudo chroot /dev/sda1". It said "Not a directory".


Oops, I said it wrong! You need to mount /dev/sda1 to somewhere, say /ubuntu, and then do the chroot:

sudo mkdir /ubuntu
sudo mount /dev/sda1 /ubuntu
sudo chroot /ubuntu

---

### Post by anklebone12 on 2010-03-08
> **kamallneet said:**
> Oops, I said it wrong! You need to mount /dev/sda1 to somewhere, say /ubuntu, and then do the chroot:

sudo mkdir /ubuntu
sudo mount /dev/sda1 /ubuntu
sudo chroot /ubuntu

ok, did that. then did the metacity command, then this came up about 30 or 40 times.

)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally with the following error: EOF in dbus-launch reading address from bus daemon


Is this bad? I doubt it's supposed to happen.

---

### Post by anklebone12 on 2010-03-08
Also when I tried recovery mode, xfix wasn't an option. Why wasn't it there??

---

### Post by kamallneet on 2010-03-08
> **anklebone12 said:**
> ok, did that. then did the metacity command, then this came up about 30 or 40 times.

)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally with the following error: EOF in dbus-launch reading address from bus daemon


Is this bad? I doubt it's supposed to happen.

I think it's normal. The metacity command seems to require a running GNOME, which is not the case in recovery mode. I suggest that you just remove compiz for now. After the chroot, give this command:
sudo apt-get purge compiz compiz-plugins

By the way, when does your system freeze? Before you login, or after that?

---

