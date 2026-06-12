---
title: "&quot;errors were found on&quot;....serious file system issue"
date: 2010-08-15
forum: General Help
---

### Post by jackheart on 2010-08-15
Well I installed Ubuntu 10.4 LTS. I did a full install since I think Dual boot was byond my capability for now.   
My partition scheme is as fallows:   
50 GB / ext 4  
1 GB /boot ext 4   
8 GB swap   
196 GB /home ext4    
 
For about a week, about once a day, I got a message saying there were errros on /boot or /home or / or something else. Then is says press F to try and Fix, M to fix manually, or S to skip this boot. So I hit F and sometimes It gets booted, sometimes it restarts. Then I can do a few reboots or shutdowns but after about a day of doing this and that, it happens again.      
 
Then about 2 days ago it would not boot at all, said something like could not locate init file then gave me a weird (to me) command line that started with init. So I tinker around online (thank god for the fast loading knopix live CD) and found out about Fsck. Sure enough running this in the ubuntu live CD did fix my system, although it did say something like &quot;0.5% non contigious&quot; (I think, sorry for not writing down.) Sure enough this fixed the problem and I was able to go right into Ubuntu except...     
 
It was really slow, like way slower then What I had going before. And after about a day, I start getting the error on disk message again. Fixed it once but now it has not worked at all. I have not run Fsck again because I think I have a more serious issue.    Not to be slanderous of ext4 supporters, I can;t help to wonder if this is the problem. I am very tempted to reinstall with ext3. I was also reading about editing the Fstab, but I wanted to post before I start messing with that.     
 
Also I do understand that 10.4 is still a bit unstable. Since I am not a programer, but rather an artist, it would be nice to run a distro that is more stable. I have a disk for Puredyne which runs 9.10 and worked great on a 9 year old Thinkpad.      
 
Thanks for the help. Any suggestions would be great. So far you all have rocked on these forums.

---

### Post by Miljet on 2010-08-15
If it were me, I would suspect that your hard disk is on its last legs. The fact that fsck fixed the problem for a couple of days and it came back would indicate this to me.

---

### Post by jackheart on 2010-08-15
to bad its a brand new computer Laptop Model: Acer 5251-1513 HD: Toshiba MK2564GSX ATA 250GB

---

### Post by jackheart on 2010-08-17
Well I did A Fresh install using the ext3 format and I have not had any problems now for a few days.

---

