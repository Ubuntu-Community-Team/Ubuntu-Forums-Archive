---
title: "Can't install kubuntu along with ubuntu"
date: 2010-06-06
forum: General Help
---

### Post by steve509 on 2010-06-06
Hello fellow forumers. I'm running ubuntu 9.10 64 bit on an amd x64 computer. I have a cd for kubuntu 9.04 32 bit that I want to try. When I reboot and the "boot from CD/DVD:" comes up I hit the enter key (sometimes many times) but it won't load the kubuntu. Anyone know what I'm doing wrong, if anything? Any help is always appreciated. I am still a newbee here.

Thanks in advance
Steve509

---

### Post by Smart Viking on 2010-06-06
Hey, i don't know the answer to your problem, but. 

You can alternatively, when you are inside ubuntu, run this command from the terminal:

sudo apt-get install kubuntu-desktop

That will install the kde, so when you log in, you can choose whether you want to use kde or gnome from "sessions". One thing to notise though, the programs that comes with the kde desktop will show up in the gnome and opposite, but you can change that by right click on Applications then hit "Edit menus". (i don't know how to do it in kde but there is a way to do it there to i think)

If you want to uninstall kde with it's program, do this:

sudo apt-get remove kubuntu-desktop

Hope this helped a little. :)

---

### Post by steve509 on 2010-06-06
Thanks, I'll give that a shot...does that mean the only difference between the 2 is kde or gnome??

---

### Post by Smart Viking on 2010-06-06
> **steve509 said:**
> Thanks, I'll give that a shot...does that mean the only difference between the 2 is kde or gnome??

Yes that and, that there is different programs. :)

EDIT: Same with xubuntu and lubuntu, xubuntu uses xfce4, and lubuntu use lxed. :)

---

### Post by steve509 on 2010-06-06
Thank you so much Smart Viking, you've been a big help.

---

