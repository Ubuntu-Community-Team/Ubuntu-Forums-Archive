---
title: "Grub problem cant boot ubuntu or windows."
date: 2009-12-19
forum: General Help
---

### Post by Pieloi on 2009-12-19
Since I'm an idiot I find myself with one problem after another.
I used to have ubuntu and windows7 on a perfect duel boot (cant remember how i did it, but it works, thats the logic), one day ubuntu spacks out, I guess its time to reinstall ubuntu...

Was in windows, deleted my old ubuntu installation/partition. (and grub went with it)
Booted 9.10 disc, Reinstalled 9.10
Grub didnt install properly. (not giving me a choice of OS, menu.lst missing, can only automatically boot into ubuntu)
[http://ubuntuforums.org/showthread.php?t=1359540&highlight=grub](http://ubuntuforums.org/showthread.php?t=1359540&highlight=grub)   followed the advice in there, grub installed. (I noticed a menu.lst hadn't generated..I restart to give it a chance)
Now when I boot my PC grub can't boot into Ubuntu or Win7, or wont automatically.
It sits there at a Grub command shell, wanting me to tell it what to do, but thats the problem..

I dont know what to do.
How can I set a duelboot back up ?

Ubuntu is located on hd0/sda5     atleast i think it is, If anyone can help me sort this mess out within atleast a couple of days I'd be grateful since I'm moving back to Sweden soon and I'd atleast want to get there with a working computer.

---

### Post by drs305 on 2009-12-19
If you did a clean install of 9.10, you are now using Grub 2. There isn't a menu.lst in GRUB 2.

Here is the community doc on GRUB 2. In addition to an introduction to G2, there are instructions on reinstalling G2 and booting from the Grub prompt. 
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

To see the menu during boot, with G2 you hold down the SHIFT key. Otherwise it is designed to boot directly into linux if it isn't aware of other OSs.

Here is another link that may be helpful to you:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Leppie on 2009-12-19
if ubuntu is on /dev/sda5, you can try this:
```
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro		
initrd /initrd.img		
boot
```

---

### Post by Pieloi on 2009-12-19
if you meant do those commands at the grub shell, non of them worked, reporting error 27 on everything.
Attempting to do root at any point resulted in grub saying every single partition did not exist, even 5.
it knows hd0 exists.
attempting boot will result in a fairly obvious "Must load kernel first" error.

pressing/holding shift did not show a list of operating systems to boot from, or even a response.

from my view this is how Im guessing things stand, if it sheds some light on the situation)
hd0 (500gb)
sda0(370gb or so) 
sda1(80gb windows 7 boot)
sda5(14gb ubuntu)

---

### Post by john newbuntu on 2009-12-20
It will help us if you can post the output of running meierfra's very popular and useful script to diagnose boot issues. Using a liveCD, run this command from a terminal and paste/attach the output file (RESULTS.txt in the desktop folder)

```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.41/boot_info_script041.sh/download' \
&& chmod 755 boot_info_script041.sh \
&& sudo ./boot_info_script041.sh
```

---

### Post by Leppie on 2009-12-20
boot from a livecd and reinstall grub to the mbr of your disk:
```
$sudo mount /dev/sda1 /mnt
$sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

