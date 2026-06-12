---
title: "No keyboard/mouse at login screen ..."
date: 2012-05-28
forum: General Help
---

### Post by Bucky Ball on 2012-05-28
Hi all,

As the title suggests ...

To cut a long story short, tried to install ATI graphics, screwed things up on next boot, spent a week trying to fix the purple screen where the login should be, and finally did by removing everything fglrx. 

That's all great and I'm getting closer; now when I boot, I get to the login screen, but the keyboard and mouse are totally unresponsive. The only way out is to hold down the power button. :(

I've searched thoroughly but nothing I've found has fixed. All suggestions welcome. I'm using 10.04 and have done quite a bit of tweaking throughout this saga so may have done something to kill the mouse and keyboard along the way. 

All suggestions gratefully accepted (within reason!). ;)

---

### Post by Bucky Ball on 2012-05-29
A strange thing I've noted. When I check out /etc/default/grub on 10.04 I get this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
```

... (this is what I'm using for 10.10 also which works faultlessly) but when I hit 'e' to edit the kernel line at boot, none of that is there. In fact: 

```
ro quiet splash
```

... is not even at the end of that line. I need to add:

ro single

... to boot to recovery. Maybe I'll try it with nothing and see what happens. My 11.04, which also works faultlessly, has this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

All advice and ideas gratefully accepted. Spent a week (when I had time) getting to this stage and feeling like I might be stuck here for another ...

---

### Post by Bucky Ball on 2012-05-29
Maybe someone could enlighten me on where the config for keyboard and mouse is? xorg.conf is, of course, no longer there in 10.04 and I don't have it in 10.10 or 11.04 either but they're running fine.

I'll keep digging ...

---

### Post by Bucky Ball on 2012-05-29
Cracked it. And the solution was sitting literally right in front of me. 

I spent the afternoon digging around, like most of yesterday, attempting to fix the dead mouse and keyboard. In the process of fixing the graphics I'd removed /etc/X11/xorg.conf.d from the 10.04 install ... which I realised after two or three hours of research, is the directory containing all the files I need to get the mouse and keyboard working! 

The xorg.conf.d directory was right there on the 10.10 desktop all along (at least, rather than trashing it, I had the sense to keep it in a safe place in case it was a mistake removing it). As the graphics fix had taken a week or so, on and off, I'd forgotten it was even there.

For some reason wouldn't let me just copy the directory from my Desktop to the /etc/X11 of the 10.04 partition so I opened file manager as root with 'gksu' and created the directory (/etc/X11/xorg.conf.d) and copied the files into that. (Incidentally, it wouldn't let me sudo cp the directory over either or let me do with file manager opened as root.)

Restart, boot 10.04, she's apples, as we very rarely say nowadays in Australia, but this is a special occasion ... pretty much as was; slick, fast, unobtrusive Xubuntu. In fact, it's better, because I've just spent the last three hours carrying on where I was a week and a half ago; configuring and tweaking the install to my liking as this is where I'll be living for the next year. ;)

Ok, thanks, solved. Hope it helps someone. And incidentally, my kernel line has nothing on the end. No ro, quiet, splash, or anything else. Sweet. Seems to be running faultlessly.

---

### Post by David Andersson on 2012-05-29
Good that you solved it, and nice that you shared your story with us. (Tell me to remove my post if you want to be alone.) In hindsight, no, in restrospect, no, anyway: did you use update-grub to make changes to /etc/default/grub stick?

---

### Post by Bucky Ball on 2012-05-29
> **David Andersson said:**
> Good that you solved it, and nice that you shared your story with us. (Tell me to remove my post if you want to be alone.) In hindsight, no, in restrospect, no, anyway: did you use update-grub to make changes to /etc/default/grub stick?

```
sudo update-grub
```

... generally, but as I was in via recovery mode and root, the sudo was not required.

I didn't actually make any changes to grub, though. I just looked at the two grub files. ;)

I was only adding 'ro single' at the kernel list at boot to get into recovery (and didn't want it to stick) but now the graphics and mouse/keyboard problems are fixed 10.04 seems to require nothing to boot normally. The kernel line has nothing at the end but the file actually looks like:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
```

Go figure. Not sure what's happening there but all is running well regardless ...

---

