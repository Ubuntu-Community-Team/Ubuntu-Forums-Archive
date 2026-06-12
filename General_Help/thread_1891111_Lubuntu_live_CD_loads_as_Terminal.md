---
title: "Lubuntu live CD loads as Terminal"
date: 2011-12-04
forum: General Help
---

### Post by xtgyal on 2011-12-04
I sucessfully installed Lubuntu on an old laptop (512 MB RAM, 1.5 GHz CPU), but there is some kind of issue with the computer and it keeps freezing or crashing every few minutes.  I tried loading Lubuntu as a live CD (from the same disc I already installed on the hard drive with) to see if I can bypass the hardware issues and it was working fine that way for a bit, but now whenever I try to load it live it loads as a Terminal, with no GUI.  What might be going on here?  The disc itself is fine, I've checked that.

---

### Post by mikewhatever on 2011-12-04
Probably something to do with an old GPU like Intel 8xxx.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by oldtimer7777 on 2011-12-04
> **xtgyal said:**
> I sucessfully installed Lubuntu on an old laptop (512 MB RAM, 1.5 GHz CPU), but there is some kind of issue with the computer and it keeps freezing or crashing every few minutes.  I tried loading Lubuntu as a live CD (from the same disc I already installed on the hard drive with) to see if I can bypass the hardware issues and it was working fine that way for a bit, but now whenever I try to load it live it loads as a Terminal, with no GUI.  What might be going on here?  The disc itself is fine, I've checked that.

Do you have a flash drive that you can use to boot from a Live Bootable USB of Ubuntu?

I have found those to work really well on old hardware if you are going to using them from a live image.

---

### Post by claracc on 2011-12-05
> now whenever I try to load it live it loads as a Terminal, with no GUI. What might be going on here? The disc itself is fine, I've checked that.

It is a known bug? in the 11.10 lubuntu live disc, one you have logged in in console mode you can run startx in order to have the gui.

---

### Post by mikewhatever on 2011-12-05
> **oldtimer7777 said:**
> Do you have a flash drive that you can use to boot from a Live Bootable USB of Ubuntu?

I have found those to work really well on old hardware if you are going to using them from a live image.

Many old computers' BIOS don't support booting from USB.

---

### Post by mastablasta on 2011-12-05
> **claracc said:**
> It is a known bug? in the 11.10 lubuntu live disc, one you have logged in in console mode you can run startx in order to have the gui.
 
yes it's a bug.
 
you can start instalation and then quit it and it will load the desktop.
 
see release notes for more info: [https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot)
 
[SIZE=2]>  
[SIZE=2]Desktop ISO boot to a terminal prompt[/SIZE]
 
In some cases, Lubuntu desktop ISO boots to a terminal prompt instead of the desktop session when "Try Lubuntu without installing" is chosen. You can manually start the session by typing "sudo start lxdm" ([854837]("https://bugs.launchpad.net/bugs/854837")). Or you can choose "Install Lubuntu" and once the installer starts, click "Quit" then "Quit" and you'll get the live desktop. For more information, please see [this link]("http://ubuntuforums.org/showpost.php?p=11398602&postcount=35")
[/SIZE]

---

### Post by mastablasta on 2011-12-05
> **mikewhatever said:**
> Many old computers' BIOS don't support booting from USB.
 
you can boot USB using PLOP boot manager (stick it on a CD or Floppy disk) or if you install grub to disk and modify it (not for beginners!).

---

### Post by lebamastiipaprike on 2011-12-27
Here' s problem: 

When I choose 'start lubuntu without install', it loads on terminal. When I enter 'startx' or 'sudo start lxdm' it loads black screen and black mouse arrow. 
When I choose 'install lubuntu' it doesn' t show any installation window but it behaves like in the 'start lubuntu without install' case.

I have checked the CD midsum and it' s ok. 
My machine satisfies system requirements for running lubuntu.

---

