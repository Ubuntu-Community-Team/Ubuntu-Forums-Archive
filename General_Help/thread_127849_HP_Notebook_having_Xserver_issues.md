---
title: "HP Notebook having Xserver issues"
date: 2006-02-10
forum: General Help
---

### Post by BryanG on 2006-02-10
Hey,

I'm a noob to Linux, and not doing so well. :( 
I installed Ubuntu, but the GDM will not load, saying that the Xserver is down.  It then will only go into command mode.  I have run sudo dpkg-reconfigure xserver-xorg, but with no luck.  I have an ATI Radeon XPress 200M graphics card in my HP ze2115us notebook.  My main question is, how do I download the ATI graphics in only command mode?  Is there anything else I should be trying?  Otherwise, I am ending up with an $800 paperweight.

Thanks,
BryanG

---

### Post by thekiller on 2006-02-10
[QUOTE=BryanG]Hey,

I'm a noob to Linux, and not doing so well. :( 
I installed Ubuntu, but the GDM will not load, saying that the Xserver is down.  It then will only go into command mode.  I have run sudo dpkg-reconfigure xserver-xorg, but with no luck.  I have an ATI Radeon XPress 200M graphics card in my HP ze2115us notebook.  My main question is, how do I download the ATI graphics in only command mode?  Is there anything else I should be trying?  Otherwise, I am ending up with an $800 paperweight.

Thanks,
BryanG[/QUOTE]

Whats the error ? And if u can post your xorg.conf, it would be great !

---

### Post by WildTangent on 2006-02-10
That chipset doesnt work. I have a Radeon Xpress200 in my A64 desktop, no luck either. Don't think anyone's gotten it working.

-Wild

---

### Post by RAOF on 2006-02-10
You should be able to get it sortof working using the VESA graphics drivers.  When it spits you back to the command prompt, run "sudo dpkg-reconfigure xserver-xorg".  It'll ask a bunch of questions (the defaults are fine, unless you know better), and one of them will be a list of graphics drivers.  Yours will probably be on "ati".  You want to select the "VESA" one.

Once you're done, run "sudo /etc/init.d/gdm restart" to get to the GUI.  Then you can try fixing it for real with the "ATI drivers" link in my sig.

---

### Post by Gentleman on 2006-02-10
Hi, 

I have the sollution... Had the same problem and it is not that difficult to solve... (Aldoh you loose 128mb ram... - Maybe ati will fix this issue soon)

A. go to the bios and enable uma (you'll have 128mb sideport and 128mb UMA)
without this the fglrx-driver wont work...

B. follow the ati-fglrx-guide on this forum ([http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584))

- I advice to recompile the kernel for your hardware with a 2.6.14+ before you setup the drivers.
- I also advice to install ubuntu after the change in the bios is done...

Succes!
(I have a hp pavillion zv6000 and it works perfectly)

---

### Post by BryanG on 2006-02-10
Hey, the VESA driver did work after rebooting my computer, but not with the sudo /etc/init.d/gdm restart.  IDK why, but hey, it works.\\:D/ 

I found the post on the ATI drivers earlier, but was wondering how to download them from the command prompt.  Now that Ubuntu works, I can fix it.  Thanks, everyone!

---

