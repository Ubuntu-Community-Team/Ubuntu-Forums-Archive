---
title: "GNU GRUB v.1.97~beta4  re-booting problem"
date: 2010-03-24
forum: General Help
---

### Post by mcGyverTV on 2010-03-24
Just a beginner here... I recently was prompted to upgrade various files and selected Go.... when upgrades were completed the system shut down to re-boot but stopped at a terminal prompt I am not familiar:
 
sh:grub> 
 
Can Someone help me past this??

---

### Post by drs305 on 2010-03-24
Do you know which version of Grub you are using? Your computer is not currently finding the Grub boot files. 

If you are using Grub 2 (if you know) you can try to boot from the Grub 2 command line following the instructions found here:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

If you aren't able to boot or need more help, please run the boot info script linked below after booting to the LiveCD Desktop. When you are ready to post the results, click on the # icon in the post's menu so you can paste it between "code" tags.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by mcGyverTV on 2010-03-24
At the top of my screen it says GNU GRUB version 1.97~beta4 ...

---

### Post by drs305 on 2010-03-24
Ok, that is Grub 2, so you can try booting from the Grub 2 command line as detailed in the link provided in the previous post, or give us the results of the boot info script to allow us to see what may be happening.

---

### Post by mcGyverTV on 2010-03-24
Thanks for the tips... Sorry, But I am as Green as they come ... I looked into your suggestions and am still reading Greek .... 
 
As suggested, Can I give you my results of the "boot info script" so that you may see what is happening? Here is what shows on my screen below:
 
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]
 
sh:grub>

---

### Post by NNing on 2010-04-18
hey mcgyver,

i know where you're coming from re reading greek.

here's a link i found cos i've got the same problem.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

won't be able to help you more than that... won't try fixing it myself till the desktop is back up & running. (it was also stuffed because of an incompatibility issue with graphics drivers and ubuntu. i've tried time & again to go with freeware ubuntu cos the idea is great but have really had a gutfull. i give up. ubuntu wins. big corporations will be on the software scene for a while to come it seems.)

---

