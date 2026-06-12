---
title: "Ubuntu 10.4 fails to boot up"
date: 2010-07-28
forum: General Help
---

### Post by altruist77 on 2010-07-28
Hi,
    I have a laptop with Windows 7 and Ubuntu installed in seperate partitions. When I boot up the computer I get options to boot either in windows 7 or Ubuntu. Yesterday I updated Ubuntu to 10.4 version. I have been having issues with grub rescue, which was rectified an hour ago. Now I can boot up into windows 7, but when I try to boot into Ubuntu, I get a GRUB screen as below:
```
GNU GRUB Version 1.97~beta4
[Minimal Bash-like line editing is supported. For the first words TAB lists possible command completions. Anywhere else TAB lists possible device/File completeions.]
sh: grub>
```When I type 'ls' I get the following list
(loop0) (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) 

Please help me to restore Ubuntu. I have no prior knowledge about the command prompt scripts. Kindly help me through with some patience.
Thank you
Best wishes
Arul

---

### Post by quixote on 2010-07-29
Grub has just lost track of where your ubuntu OS is and wants to be told.  That grub> prompt is just grub's way of saying "I don't know what to do next."  The following is all taken from here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode) which has a lot more information you can refer to. 

If you know which is your ubuntu partition, then you don't need this step.  If you don't, use that ls command but direct it to a specific partition:```
ls (hd0,2)/
```. If that's your ubuntu partition, it'll have files with vmlinuz and initrd in the file name. If it's not there, try ls (hd0,3)/, and so on. (hd0,1) is probably your Windows install.  Make a note of where the ubuntu OS is.

Then enter the following commands at the grub> prompt. (Comments in italics.)
```
**set root=(hd[COLOR="Blue"]X,Y[/COLOR]**)
     *substitute your correct drive numbers*
**linux /boot/vmlinuz-[COLOR="Blue"]<your version>[/COLOR] root=/dev/sd[COLOR="Blue"]XY[/COLOR] ro**
     [I]you can hit TAB at the hyphen and it will show you the possible completions. 
      When there is only one choice, it'll autocomplete the entry.  
      The root=/dev/sdXY entry uses the usual linux conventions, so if, for instance, 
      your ubuntu is on the second partition, that would be /dev/sda2 [/I]
**initrd /initrd.img**
**boot**
```

Those changes don't persist between bootups.  Once you've booted successfully, You need to open a terminal (Applications > Accessories >Terminal) and type ```
sudo update-grub
```

I hope it all works the first time you try it! :D

---

