---
title: "&quot;module not found.Aborted. press any key&quot; message at boot. No grub"
date: 2010-07-11
forum: General Help
---

### Post by art20 on 2010-07-11
I just got a m15x alienware and I decided to install ubuntu on it alongside Win 7 (64 bit). 
I only have 1 320GB hard drive on the laptop so I made a 40gb partition for linux.
Everything went well during installation, updating and configuration, I was pretty happy with both systems running until I booted into windows and then when I tried to boot back into linux I got the "module not found. Aborted. press any key" message.

I couldnt reinstall the grub from the live CD (mostly because I dont know how) so I did the /fixboot /fixmbr and /rebuildbcd commands from the windows recovery cd to be able to boot back into windows but this made the ubuntu partition unbootable.

This process has happened about 5 times and I have tried to update the grub first thing after installation and I still have the problem. After reading some on these forums I downloaded the boot info script and these are the results 

[ATTACH]163140[/ATTACH]
and this is the output of fdisk -l
[ATTACH]163139[/ATTACH]

---

### Post by art20 on 2010-07-11
Bump! >.< Sorry I rly need help with this, I dont want to have to install Ubuntu everytime I want to use it -.-

---

### Post by HenneBaby02 on 2010-07-11
"I couldnt reinstall the grub from the live CD (mostly because I dont  know how) so I did the /fixboot /fixmbr and /rebuildbcd commands from  the windows recovery cd to be able to boot back into windows but this  made the ubuntu partition unbootable."


I'm pretty sure windows Bootmgr only loads windows when you split partitions, u more likely figured that out though lol and grub boots both... 

Your Best bet is to Use "Wubi" which installs ubuntu right into windows C:\ Drive or whatever drive u installed windows too.. and u can easily switch between windows and ubuntu.

If you open your ubuntu.iso from windows you`ll see a Wubi.exe file which is the installation file.. or you can just download it and it will download whichever ubuntu you want.. only the latest though (10.04)


So if you have free time on your hands just reinstall windows 7 and put all 320GB towards it.. then after u install windows and the basics use the Wubi and install ubuntu... then when u restart ull have these options


Windows 7 (whatever edition)
Ubuntu

Then when u select Ubuntu, Grub will show up..

From experience i also seem to have some type of problems when it comes to splittin the partitions and the fact that people in this house barely know where to find the start menu lol... But enough rambling i hope that works out for you


EDIT: I forgot to mention if that extra 40 GBs is no big deal for you... use your windows CD again and boot from it, when you get to the partitions part.. delete the ubuntu partition.

---

### Post by art20 on 2010-07-11
> **HenneBaby02 said:**
> "I couldnt reinstall the grub from the live CD (mostly because I dont  know how) so I did the /fixboot /fixmbr and /rebuildbcd commands from  the windows recovery cd to be able to boot back into windows but this  made the ubuntu partition unbootable."


I'm pretty sure windows Bootmgr only loads windows when you split partitions, u more likely figured that out though lol and grub boots both... 

Your Best bet is to Use "Wubi" which installs ubuntu right into windows C:\ Drive or whatever drive u installed windows too.. and u can easily switch between windows and ubuntu.

If you open your ubuntu.iso from windows you`ll see a Wubi.exe file which is the installation file.. or you can just download it and it will download whichever ubuntu you want.. only the latest though (10.04)

Thanks Ill give that a try and let you know how it went

---

### Post by art20 on 2010-07-13
Ok so I reinstalled Ubuntu using wubi and all seems to work just fine, it kind of worried me that during the installation it said that isntalling it this way would probably cause it to run a little slower but so far it runs without a glitch... the only thing that concerns me now is that internet is painfully slow using firefox... just to give you an idea its taked over 12 hours to download chromium. I find this very strange because the speed to download packages is normal, it's just really slow when browsing the web, trying to figure out if its the browser or the network card.

Anyways, thanks a lot for your help. :)

---

