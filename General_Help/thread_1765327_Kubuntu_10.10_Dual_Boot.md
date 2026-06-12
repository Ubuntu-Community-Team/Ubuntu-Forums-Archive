---
title: "Kubuntu 10.10 Dual Boot"
date: 2011-05-22
forum: General Help
---

### Post by Jerry N on 2011-05-22
I installed Kubuntu 10.10 as the second OS in a dual boot setup so Kubuntu obviously the default OS.  Where in Kubuntu can I change the boot order so that the other OS(Mint 11 in this case) is the default?  I am used to Gnome where it is quite simple.

Jerry

---

### Post by Jerry N on 2011-05-23
> **Jerry N said:**
> I installed Kubuntu 10.10 as the second OS in a dual boot setup so Kubuntu obviously the default OS.  Where in Kubuntu can I change the boot order so that the other OS(Mint 11 in this case) is the default?  I am used to Gnome where it is quite simple.

Jerry

I guess (a) no one knows or cares, or (b) it can't be done or (c) I'm too old or stupid to figure it out for myself.  Oh well - I haven't liked any version of KDE since Freespire died out but I thought I would try it again.  Bad idea.

Jerry

---

### Post by Jerry N on 2011-05-23
And if anyone cares, Pinguy Linux seems to have left out the capability to select a different default OS too.  I am sure this can be accomplished by modifying a configuration file somewhere but this is 2011, not 2001.

Jerry

---

### Post by enimeizoo on 2011-05-23
To help you we need to know wich bootloader you have.
I don't know what is mint's bootloader, so I'll assume it is grub2. You can figure it out by running
```
grub-install -v
```A version number higher than 1.96 means grub2. 
If so, the file to edit is /etc/default/grub
You have to change the value of GRUB_DEFAULT
You can designate an entry by its number (0 for the first one), by its exact name (between double quotes "name").
If you want the default to be the last one used, set this to true :
```
GRUB_SAVEDEFAULT=true 
``` 
You need root permission to edit the file, and once done, you need to run :
```
sudo update-grub
```Let me know if your bootloader is not grub2.

---

### Post by Mr. Shannon on 2011-05-23
You could try installing **startupmanager**.  Then it will be as easy to change the default OS booted by grub with as it was with Gnome.  I assume startupmanager will run in KDE.

---

### Post by enimeizoo on 2011-05-23
I didn't know about that. I just tested, it does run in kde. It is a lot easier, actually.

---

### Post by Jerry N on 2011-05-23
> **Mr. Shannon said:**
> You could try installing **startupmanager**.  Then it will be as easy to change the default OS booted by grub with as it was with Gnome.  I assume startupmanager will run in KDE.

That rings a bell - I think I used startupmanager sometime in the past.  Doesn't make any difference now, I have already eliminated the Kubuntu install.  I don't know that I think recent versions of KDE are slow but I just feel like I am swimming upstream in quicksand whenever I try to do anything.  I don't like Pinguy any better and it is supposedly gnome.  Right now, I find that Mint 11 (RC) works really well.

Jerry

---

### Post by SeijiSensei on 2011-05-23
Look for the "default" setting in /boot/grub/grub.cfg.  It's set to zero at installation, which boots the kernel in the first stanza.  If you want to make the second stanza entry the default, set the value to one.  (In *nix, counting often begins with zero.)

You'll need to edit this file as root with sudo.  You'll also need to change its permissions since by default it's read-only:

```

cd /boot/grub
sudo chmod u+w grub.cfg
sudo nano grub.cfg
sudo chmod u-w grub.cfg

```

---

