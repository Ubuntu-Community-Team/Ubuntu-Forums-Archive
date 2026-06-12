---
title: "Ubuntu has goosed my Windows drive!!"
date: 2010-10-21
forum: General Help
---

### Post by DitchingMS on 2010-10-21
Hi guys

I'm desperate here and struggling to find a solution in the forums.

I have two identical 500gb SATA hdd's installed on separate channels. They are not RAID etc. I never use on of them in fact! Having some time free I decided I would install the latest version 10.10 Ubuntu on the second HDD, leaving my Windows install and all of my files partitioned on the first drive. Therefore Drive #1 has four partitions on it with Windows, work, etc. and Drive #2 was newly formatted by the LiveCD and I installed 10.10. I used to have 9.04 installed on Drive #2 and I would boot it by changing the boot sequence in the BIOS, keeping the drives totally separate for security.

When I restarted at some point after a successful 10.10 install, I got the grub screen (good I thought!) but selected Windows instead of Ubuntu. Just as Windows was about to load I got a BSOD (about a graphics driver I think). Thinking that the new install was a problem, I changed the boot sequence and eventually ended up with Windows refusing to boot AND 10.10 refusing to boot. Simple solution in hindsight - grub 2 installed on the wrong drive! However - I ended up somehow with grub telling me a device was missing with a string of crazy characters, then NTLDR was missing, so I ran fixmbr and fixboot on my Windows drive, THEN I was told it had an Invalid Partition Table! I have since run all sorts of drive management tools and all of them say that Drive #1 is just one big unknown filetype partition. The best they can do is to format it!

This might seem reckless but I have always relied on having separate partitions on my HDD to cope with a broken OS. However I cannot afford to lose the whole HDD as it has all of my things on from about the last 15 years! Please tell me I can salvage the partitions and fix the partition table - in a Windows or Linux environment - and for free!!

By the way next time I will back up my drives.


EDIT - I have since purged and reinstalled Grub 2 on Drive #2 and Ubuntu is back up 100%. However Windows and all my work is still gone.

---

### Post by Quackers on 2010-10-21
The only thing I can think ofn is to try testdisk, which is available through synaptic package manager. Several people have had excellent results reclaiming drives with dodgy partition tables. Good luck.

---

### Post by yetiman64 on 2010-10-21
> Please tell me I can salvage the partitions and fix the partition table+1 for testdisk, here is a link to a step by step guide if you do end up using it. 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Mark Phelps on 2010-10-21
I've found, through painful experience, that MS Windows apps do a much better job at recovering NTFS partitions and files than do Linux utilities.

If it were my data (and it HAS been before), I would go to the Runtime Software site, download their trial versions of GetDataBack for NTFS, and Recover My Files, install them on an MS Windows box, plug in my damaged drive to that box as an external drive, run the utilities overnight -- and see the next day how good a job they did of finding my files.

You could also do the same kind of analysis using Testdisk, but my personal experience using that on NTFS volumes has not been good.

If the Runtime Software utilities do a better job than Testdisk, it's your decision regarding whether it's worth buying their product to recover your 15 years worth of files.

---

### Post by DitchingMS on 2010-10-21
Thanks all for your quick and helpful replies! I've worked on this all day and - up to now - Ubuntu is still going strong.  I had heard about TestDisk before but that it was quite simplistic and wouldn't really help - wrong, it was excellent and I believe it recovered the information. The only snag is, although the windows partitions seem to be there and the data is apparently accessible, chkdsk threw up a lot of errors and I think made a few changes. I'm a bit worried some of my data might have been a bit mothballed. Anyway, I'm still being positive and the only error I know is still there is that Windows boots all the way through then just before it's about to open the GUI it BSODs with an error on ext2fsd.sys - tantalising! Little help please?

Thanks

---

### Post by yetiman64 on 2010-10-21
> **DitchingMS said:**
> Thanks all for your quick and helpful replies! I've worked on this all day and - up to now - Ubuntu is still going strong.  I had heard about TestDisk before but that it was quite simplistic and wouldn't really help - wrong, it was excellent and I believe it recovered the information. The only snag is, although the windows partitions seem to be there and the data is apparently accessible, chkdsk threw up a lot of errors and I think made a few changes. I'm a bit worried some of my data might have been a bit mothballed. Anyway, I'm still being positive and the only error I know is still there is that Windows boots all the way through then just before it's about to open the GUI it BSODs with an error on ext2fsd.sys - tantalising! Little help please?

Thanks
You could possibly try booting into Windows safe mode (the ext2fsd.sys is an ext2 file system driver and won't be loaded in safe mode - seems it is the BSOD culprit) and do a removal of that driver (then do a reboot into Windows normally) just to check that Windows itself is OK.

BTW sounds like Ubuntu didn't actually goose your drive but a Windows driver you installed in Windows for ext filesystems access did ;). Good luck

---

### Post by DitchingMS on 2010-10-21
Thanks Yeti, I had the same idea but safe mode hung after loading loads of drivers. I think the last one it loaded was mup.sys which I *think* often takes a while, but it was like ten mins or something. I also managed to get the Windows boot menu to run 'last known good configuration' and used testdisk to overwrite the boot sector with the backup - although I'm not sure if either helped. On a positive note, at least the Windows loading screen is normal up until the GUI loads.

I may try safe mode again just in case but in the meantime I thought I'd boot onto Drive #2 and use Ubuntu to scan for all files containing ext2fsd or grub. Nothing found so I don't know how to remove it from outside Windows.

I do have some software installed to read ext drives using a virtual machine within Windows but it hasn't caused problems before. After the first problem of grub installing itself apparently to the Windows drive I assumed that was the culprit.

---

### Post by yetiman64 on 2010-10-21
Ah Ok it may be related to the grub issue then. Hope you find a fix for this, I am currently out of ideas at the moment. Will keep an eye on the thread to see how it goes. Cheers for now and Good Luck. yetiman64

---

### Post by DitchingMS on 2010-10-22
Good news, touch wood I have fixed all of the problems and got my work back! I tried Windows safe mode again and I was right it does take ages to load mup.sys, about 15 minutes I think, but I got in, uninstalled two ext2fsd programs, booted up today and we're back! Fingers crossed I don't find in six months that something is missing or corrupt...

I don't want to say for definite what caused the BSOD but grub definitely installed itself on the Windows drive so purging and reinstalling was a good call.

I'd now like to devote part of Drive #2 to a backup area where I can back up my private work. On my experience of having damaged Ubuntu installs multiple times before with downloaded drivers I may also create a second Ubuntu install on Drive #2 as well - that way I can always read the contents of the drive.

If anyone has any tips on this please let me know - otherwise thanks for all your help!

---

