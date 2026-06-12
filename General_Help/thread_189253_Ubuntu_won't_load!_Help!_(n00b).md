---
title: "Ubuntu won't load! Help! (n00b)"
date: 2006-06-05
forum: General Help
---

### Post by ramcosca on 2006-06-05
I'm new at Ubuntu and Linux, so please have a little patience (started using them today, first time). I encountered a little problem... gonna make the story short.
I was *trying* to do the win32 codec install, trying a few times without being able to do so. Noticed the system a bit sluggish, don't know why. Firefox was being jerky, also.
I decided to do a reboot but the Quit menu only showed the Hibernate option, no Restart or ... whatever the turn off option is called.
I force-shut down the laptop by pressing the power button for a few seconds and then hit it again for it to boot. When the word [COLOR="Red"]Compaq[/COLOR] get out of the display (so it starts really booting), the following appears on screen:
> GRUB Loading stage1.5.

GRUB loading... please wait...
Error 15
Nothing else appears on screen, nothing else happens. It's done it about 5 times, so I'm guessing I shouldn't insist much.

[FONT="Arial Black"][SIZE="5"][COLOR="Red"]Help![/COLOR][/SIZE][/FONT] :cry:

---

### Post by monchichi on 2006-06-05
Weird.. it seems like grub isnt finding the linux kernel. Not good. You could boot from a Live CD and try to fix it, or reinstall Ubuntu. 

As far as the reboot option, you need to configure your display manager (gdm). run "sudo gdmsetup" in a terminal and make sure "show actions menu" is checked.

Next time, try installing w32codecs and what not using the following: [http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")

good luck.

---

### Post by ramcosca on 2006-06-05
Thanks for the answer. I'll keep all those in mind, including EasyUbuntu.

I might do a reinstall of Ubuntu, since I just installed it today and really didn't have anything important, just a few programs I picked to install.

Thanks again.

---

### Post by Abild on 2006-06-05
Installation of w32codecs shouldn't be that hard anyway.

Run 
sudo gedit /etc/atp/sources.list
and add the following line to the end of the file:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Run 
sudo apt-get update
and
sudo apt-get install w32codecs

libdvdcss2 for reading encrypted dvd's are in that repository as well :)

---

