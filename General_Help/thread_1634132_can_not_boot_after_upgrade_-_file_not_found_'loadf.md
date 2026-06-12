---
title: "can not boot after upgrade - file not found 'loadfont'"
date: 2010-11-30
forum: General Help
---

### Post by leon_chame on 2010-11-30
**Can not boot after upgrade - file not found 'loadfont'** 			
 			 			 		   		 		 		Hello,

I have a 10.04 system that I installed the update for. Instead of doing the restart now option I choose to do a shutdown and upon a reboot I get an error and can not boot into Ubuntu.

The error I get is:

file not found 'loadfont'
unknown command

And I get into an endless cycle of it if I try to boot into Ubuntu..can boot into windows fine as this is an Wubi install.

Does anyone have a fix for me?  This is on a work computer and I need a fix immediately.

I have read about the Wubi issues with 10.10 but this is 10.04 not 10.10...?

Thanks!

---

### Post by egkeat on 2010-11-30
Same thing just happened to me...

---

### Post by SATANiAN666 on 2010-11-30
I've found easy solution for this problem.

If WUBI won't boot, perform steps to mount your root.disk using Live CD(In my case I have root.disk mounted to /mnt/wubi)
Mounting root.disk:
1) Boot Ubuntu Live CD
2)  $ sudo mkdir /mnt/win
    $ sudo mount /dev/sda1 /mnt/win
    $ sudo mkdir /mnt/wubi
    $ sudo mount -o loop /mnt/win/ubuntu/disks/root.disk /mnt/wubi

Workaround: 
1) Move your /etc/grub.d/00_header to another folder (eg. backup)
    $ sudo mkdir /mnt/wubi/etc/grub.d/backup
    $ sudo mv /mnt/wubi/etc/grub.d/00_header /mnt/wubi/etc/grub.d/backup/

2) Start Synaptic and reinstall grub-pc to generate new grub.cfg
3) In Synaptic select grub-pc and grub-common to Lock version using Package menu
4) Reboot

Everything should work now and Grub won't be updated to preserve this change.

Tested on my Ubuntu 10.04 

PS: Sorry for my bad english.

---

### Post by bcbc on 2010-11-30
Get it booting:
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5) (You need to edit the grub.cfg for version 10.04.1). 

Permanent fix after following the above workaround:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

To recover data from windows use a tool called [ext2read]("http://ext2read.blogspot.com/") and point it at c:\ubuntu\disks\root.disk

---

### Post by leon_chame on 2010-12-03
Thank you both for the replies!

@bc - I read through the whole bug which took quite a while and very honored that you spent so much time to getting this resolved...THANKS!

---

### Post by bcbc on 2010-12-04
> **leon_chame said:**
> Thank you both for the replies!

@bc - I read through the whole bug which took quite a while and very honored that you spent so much time to getting this resolved...THANKS!
You're welcome - hope you get it sorted out.

---

