---
title: "Drives not listed after removing raid, works in Windows 7"
date: 2010-10-29
forum: General Help
---

### Post by Gizmoduck81 on 2010-10-29
I have two 1.5TB hard drives (neither one are my OS drives) that don't show up under "Places", but are detected under "Disk Utility". I tried to reformat them, but Ubuntu tells me that they are in use (even they are not mounted). gparted also detects them and shows them as being NTFS parition. I have deleted and repartitioned to NTFS as well. This works until I restart my computer. The funny thing is that Windows 7 sees them just fine. More detail as to how this happened below after system specs.
 
System:
 
AMD Phenom II x 4 955
ASUS M4A79XT EVO motherboard
8GB DDR3 1333 
1 500GB WD SATA drive (dual boot Windows 7 & Ubuntu 10.10)
2 1TB WD SATA drives (extra storage)
2 1.5TB Seagate SATA drives (extra storage, these are the problem children)
 
Here's how I got here:
 
Installed a dual boot w/ Windows 7 and Ubuntu 10.10. Everything was fine and ALL drives showed up and were mountable in Ubuntu. I decided to set up a RAID 1 w/ my two 1.5TB drives. I restarted, changed my SATA to be RAID instead of IDE and created my RAID 1. I then realized that through this motherboard's RAID setup, I couldn't have it copy files from one disk to the other to set up the mirror. So, after I rebooted and the RAID started building, I cut the power and unplugged my drives in a desparate attempt to keep my data. I then went back into the bios and set my SATA back into IDE instead of RAID. I was able to back up my data, but this is when the problem started.
 
Again, Windows 7 sees and uses the drives just fine. I copied the data I wanted from my 1.5TB drives to my 1TB drives and restarted into Ubuntu. But, no 1.5TB drives appeared under Places. I started Disk Utility and confirmed that Ubuntu does actually see the drives. However, it still lists them as being part of a RAID array (I did delete my RAID array properly through the BIOS after backing up my data). I'm not sure why it thinks that and I believe that's my problem. Also, Disk Utility lists a THIRD 1.5TB drive under "USB and Peripherals". Could that be my MB telling Ubuntu that a RAID is still set up even though I deleted the RAID pair?
 
 

What I have tried:
[LIST]
[*]Reformatted drives via Windows 7 as NTFS. This completed but didn't solve my problem.
[*]Repartitioned the drives with gparted as NTFS. This works until I restart my computer.
[*]Attempted to reformat under Ubuntu, but it gives me an error saying the drives are busy.
[*]Reinstalled Ubuntu (but didn't reformat). Didn't work.
[/LIST]What I'm thinking:
[LIST]
[*]Flash my BIOS so my MB starts out fresh and hopefully doesn't tell Ubuntu I have a RAID anymore.
[*]Reinstall Ubuntu again (this time reformatting my OS drive).
[/LIST]Anyone have ideas as to what's going on? FYI I'm new to Ubuntu.

---

### Post by ronparent on 2010-10-29
Once drives get used and configured as fakeRAID drives they have data written to a meta data section of each disk. This data does not disappear when the raid is turned off in bios and the Ubuntu dmraid utility continues to recognize those drives as raid. Performing a complete low level reformat of these disks would be one way to remove the data. Easier would be to simply use dmraid to erase the data from each drive. The command is 'sudo dmraid -E -r /dev/sdX' where X is the previous raid drive in question (a, b, c etc). Some people advise uninstall dmraid. I don't like that solution all by itself because if not removed the meta data may well trouble you again when you have forgotten about it - especially if you actively install OS's, remove them and repartition often. Do let us know if this works.

---

### Post by Gizmoduck81 on 2010-10-29
Thanks! That seems pretty simple. I'll give it a try tonight and will post my results.

---

### Post by Gizmoduck81 on 2010-10-30
This worked! Thanks again!

---

### Post by ronparent on 2010-10-31
Glad to hear it is solved for you. Good luck.

---

