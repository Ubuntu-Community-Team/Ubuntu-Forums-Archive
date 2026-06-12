---
title: "windows can't open folders copied under ubuntu in ext. HDD"
date: 2009-11-04
forum: General Help
---

### Post by kiler_4o on 2009-11-04
Hello, I decided to try Ubuntu... 
 
I had about 20GB free in my C: drive, so in ubuntu setup I used 15 of them to create a new partition for it. After I "played" a bit with it - I decided to go to windows, cuz I needed to run a program, that I didn't have in linux... So - Tried to go back, but couldn't ... some files were missing and my PC just did a reset every time it was near the welcome screen... Tried to run a program, that my PC offered me, to fix it... but no success... so I decided to do a clean reinstall... I installed windows 7, but before doing it - I copied all my info from C: and D: to my ext. HDD in linux... Installed win7, but now I can't access these 2 dirs... 
When I open their properties - it shows me, that they're 0.00 bytes... How can I access them, and can I do it at all ? 
 
Thanks in advance!
 
 
edit: I'm having a Toshiba A200-23k, Ubuntu 9.10 and now windows 7... Ext. HDD - Western Digital 1TB

---

### Post by aysiu on 2009-11-04
So is the external hard drive formatted to Ext3? Ext4? FAT32?

---

### Post by kiler_4o on 2009-11-04
it's NTFS... I can't open only the 2 directories - C: and D:, that I've created under linux, and copied all files from my hdd... I have some important information there :|

---

### Post by kiler_4o on 2009-11-09
ok, fixed it - the owner was root, i ran ubuntu live CD and changed it... now it's OK... not sure that was the problem, but it worked...
thanks anyway...

---

