---
title: "Tripple Boot, Win7/Ubuntu/Backtrack error"
date: 2010-05-16
forum: General Help
---

### Post by TeHaR on 2010-05-16
Hey guys,

i just got my new laptop and I wanted it to make tripple Boot.

I installed 
Win7 (sta1 and sta2) and then 
Ubuntu 10.04(sta3=/boot,hd4(extended)(sda5=swap,sda6=/) then I installed
BackTrack4 with the supplyed install.sh on sda7(also extended)
and sda8 is my data hd (also extended)

but Backtrack wont start on any of the Grub entrys (the last one was added by myself same error as on all)

I get the error: WARNING: Couldn't open directory /lib/modules/2.6.32-21-generic: no such file or directory 

that is my Ubuntu Kernel Version. I am Lost  :confused:

Attached my grub.cfg and some info about the /boot on sda7 (BT hd)

Edit: I use Grub from Ubuntu

---

### Post by TeHaR on 2010-05-16
nobody? :(

---

### Post by oldfred on 2010-05-16
I have seen several others with issues with backtack. Post this to see where everything is:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by asking-alhadat on 2011-01-14
i have sama trouble too...
copying file stack in 56&
i can't instalation btr4r2 :(

---

