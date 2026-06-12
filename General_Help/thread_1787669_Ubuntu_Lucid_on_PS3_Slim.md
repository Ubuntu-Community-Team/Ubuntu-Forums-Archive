---
title: "Ubuntu Lucid on PS3 Slim"
date: 2011-06-21
forum: General Help
---

### Post by rajivecn on 2011-06-21
I am new to Linux and Ubuntu
I have successfully Installed Ubuntu Lucid in the PS3 Slim (CFW 3.55)following instruction from http :// wiki.gitbrew.org/index.php/PS3:Linux
 All the steps are completed without any issues. 

 Once I boot the Ubuntu through Petitboot screen by selecting the options available the following message comes and system stuck s

 init: plymouth-splash main process(583) terminated with status 2
 init: plymouth main process (374) killed by SEGV signal

 Any help on solving this and booting to Ubuntu

---

### Post by Cordonsport85 on 2011-06-22
I have tryed the same, and i have the same problem.......thx

---

### Post by OhNoMyBrains on 2011-06-24
I was having the same issue, as well as plenty of trouble finding a solution. I did as much troubleshooting as I could booting with "quiet splash" and "--verbose" which led me to a "The disk drive for / is not ready yet or not present" error. That was the key for me.

My setup is not exactly the same as yours (CECHG 256MB NAND @ CFW 3.55), but here's what I stumbled onto that works (so far) for me:

"You are receiving this error message as the new udevd in Ubuntu Lucid no longer supports mounting its own /dev mount point. You will need to add the following line to your "/etc/fstab" file: 

----- SNIP ----- 
dev /dev tmpfs rw 0 0 
----- SNIP ----- "

source: [http://forum.linode.com/viewtopic.php?t=5522](http://forum.linode.com/viewtopic.php?t=5522)

Hope that helps :)

---

