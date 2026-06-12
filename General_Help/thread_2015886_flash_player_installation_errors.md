---
title: "flash player installation errors"
date: 2012-07-03
forum: General Help
---

### Post by artofshred87 on 2012-07-03
ok so i typed this in the terminal - aos87@ubuntu:~$ ```
sudo apt-get install flashplugin-nonfree
```and this is what i got - E: dpkg was interrupted, you must manually run '```
sudo dpkg --configure -a
```' to correct the problem.

when i ran ```
sudo dpkg --configure -a
``` this is what came up - aos87@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for aos87: 
Setting up sandboxgamemaker (2.6.1+dfsg-7) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing sandboxgamemaker (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sandboxgamemaker

i had tried to install sandboxgamemaker through the software center a few days ago but it got  stuck on applying changes so i just reset the computer by way of the power button and left it alone. it seems like it keeps trying to install but keeps failing, can anyone help with this situation? maybe let me know how to kill that process. [B]
MInd you i am not very familiar with linux i am still a noob, so if it is possible maybe any replies can  be dumbed down a bit, thank you

BTW, i am running unbuntu onieric ocelot 64 bit 
[/B]

---

### Post by fballem on 2012-07-03
There is a much simpler alternative. If you open Firefox and then Tools | Addons, a second panel will open in Firefox that will allow you to search for addons to install.

If you search for flash-aid, it will give you an option to install this add-on. The add-on will then manage the correct installation of flash for you. It will execute terminal commands, to which you will have to supply your password. As a bonus, it will remove any existing flash installation. The flash that is installed is directly from Adobe.

I have been using it for quite some time and it has proven to be very reliable.

I hope this helps,

---

