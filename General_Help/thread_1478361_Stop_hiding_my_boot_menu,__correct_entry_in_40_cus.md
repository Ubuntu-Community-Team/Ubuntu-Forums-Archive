---
title: "Stop hiding my boot menu,  correct entry in 40_custom"
date: 2010-05-09
forum: General Help
---

### Post by subcook on 2010-05-09
ubuntu 10.4

I am running ubuntu 10.4 only .

I assume to make the boot menu appear I have to add an entry into 40_custom file.  Not quiet sure how to make that entry,  or if it has to be positioned a certain way (new to linux,  maybe two months).

Trying to install PloP.


Thanks Guys!


-cheeers

---

### Post by philinux on 2010-05-09
> **subcook said:**
> ubuntu 10.4

I am running ubuntu 10.4 only .

I assume to make the boot menu appear I have to add an entry into 40_custom file.  Not quiet sure how to make that entry,  or if it has to be positioned a certain way (new to linux,  maybe two months).

Trying to install PloP.


Thanks Guys!


-cheeers
See grub2 link in my sig.

---

### Post by subcook on 2010-05-09
well,

when I type grub-install  it says I have v0.97,  but it has the characterists of grub2 ( like the 40_custom file for example).

I have tried to add a menu entry,  and disable the " hide bootsplash" option in tyhe 40_custom file,  but am very confident that I am not entering the command properly.  I Can't even tell if I entering the new boot menu option correctly, because my boot splash does not show up, as I only have one OS on this computer atm.


thanks guys in advance,



-cheers

---

### Post by linuxman94 on 2010-05-09
What exactly are you trying to do?  Make the grub menu show up on boot?  The version number is normal.  It is grub2 version 0.97.

---

### Post by subcook on 2010-05-09
my first stab,  would yes,  to get the boot menu to appear and to try and install PloP through that.  I have the PloP website and am actively using that as a guide to install it.

I have been trying to add an entry into my 40_custom file,  than update-grub as root,  but I must be entering it wrong.  Please bear in mind I am new to linux,  been elbows deep for about 2 months now (and love it).


-cheers

---

### Post by James78 on 2010-05-09
> **linuxman94 said:**
> What exactly are you trying to do?  Make the grub menu show up on boot?  The version number is normal.  It is grub2 version 0.97.I'm pretty sure 0.97 was just the original Grub, and 1.97+ is Grub2.

---

### Post by john newbuntu on 2010-05-09
James is right you have legacy grub.  But since you mention 'characteristics of grub2', you might have a mixture of grub and grub2.  Get rid of legacy grub and keep only grub2.

Once you do that follow post#3 in this thread to customize your 40_custom file:
[http://ubuntuforums.org/showthread.php?t=1474345](http://ubuntuforums.org/showthread.php?t=1474345)

Now, should you choose to stick with legacy grub, you would have to modify menu.lst and add PloP or of course you could add using the command line interface.  To make legacy grub show up, change the timeout parameter in menu.lst or hit escape at boot time to show the menu.  Also, if you have "hiddenmenu" enabled in menu.lst, comment that out.  To enter the command line interface, once you get the grub menu, press 'c'.

---

### Post by subcook on 2010-05-10
If someone could be so kind as to just take a screen shot,  and maybe show me exactly what to enter in 40_custom to make my boot menu appear it would be greatly appreciated.   "esc" is not working.  I very sorry to bother people everyone with such a rookie question,  and if thats the case I will never come to these forums and ask for help again.  I very new to linux and am trying to learn, and have no clue how to enter a proper bash command in this particular instance or this particular file.  If someone could just please help me with this one thing it would be greatly appreciated.



-cheers

---

### Post by subcook on 2010-05-11
Hey guys!

Hold "shift" to bring up the boot menu.



-cheers

---

