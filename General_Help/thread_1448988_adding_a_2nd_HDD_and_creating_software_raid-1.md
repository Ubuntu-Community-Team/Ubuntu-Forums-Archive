---
title: "adding a 2nd HDD and creating software raid-1"
date: 2010-04-07
forum: General Help
---

### Post by Matthew Horton on 2010-04-07
Hi everyone,

I have installed ubuntustudio 9.10 on my dell dimension 1100 desktop and im trying to setup raid-1 because i'm constantly worried that my hard disk is going to fail.

i have 2 drives. one 40gb and one 80gb. so, i created a 40gb partition on my 80gb drive and i want to raid this partition with the 40gb drive. is this possible? and am i right in thinking that i can raid everything including /boot?

many thanks,
matthew horton

---

### Post by Matthew Horton on 2010-04-07
hello again. i thought i would just try using disk utility to create a raid array between my two hard disks and it says "insufficient number of disks to create RAID-1 array".

this is really confusing because i definitely have two disks that show up in disk utility. i made sure the second drive was mounted and tried again but got the same error.

I have to type my user password to mount the second hard drive. i dont know if this has anything to do with it.

any suggestions would be greatly appreciated.

many thanks,
matthew horton.

---

### Post by Matthew Horton on 2010-04-08
I have also tried booting from an ubuntu 9.10 live cd but that did not work either. I tried it with the hard disks mounted as well as unmounted. any help would be much appreciated.

---

### Post by Matthew Horton on 2010-04-08
anyone? i've just searched for known bugs in disk utility and i couldn't find anything about the error im getting. i also tried looking for other software raid utilities but i couldn't find anything.

I came across this tutorial: [http://prefetch.net/articles/linuxsoftwareraid.html](http://prefetch.net/articles/linuxsoftwareraid.html)

but it says: "Each software RAID device that is defined in /etc/raidtab must be initialized. The  mkraid utility creates the device node, initializes all the devices that comprise the  RAID device, and starts the RAID device. Be aware that initialization with mkraid will  destroy data that currently exists on any of the devices that are specified in /etc/raidtab for that RAID device"

is it necessary to delete data from the partitions that i'll be using to create the raid array?

someone please help me! im new to linux and need to get raid working.
many thanks,
matt.

---

### Post by oldfred on 2010-04-08
Are you sure you want raid? I do not believe in raid for desktops as I think it gives a false sense of security and adds little performance.

Raid is used on servers to improve thru put and maintain uptime as with many drives one can be replaced while the system is running. Speed is improved as 5 or more drives are all processing the database or web request. But it is not used for backup. Our servers were still backed up every night to a rotating tape library with daily, weekly and monthly saved versions.

On a desktop performance is not improved much as you cannot type any faster nor is your download speed from your internet provider faster. If you do something to destroy data that you really wanted it just has two copies of the missing data. If you have good backups you can reinstall Ubuntu and recover your data very quickly. I backup to DVDs (not as often as I should:)) but I know I have saved copies that allow me to recover my important data even if I make a mistake and delete it.

---

### Post by cchhrriiss121212 on 2010-04-08
I agree, RAID is too complex for a new user, and software RAID is not all that great. You already have 2 drives, so just manually copy important files to the other disk. Software can be installed easily enough. Or just get an external drive which should only cost 20 quid or so.

---

### Post by arloth on 2010-04-08
> **Matthew Horton said:**
> Hi everyone,

I have installed ubuntustudio 9.10 on my dell dimension 1100 desktop and im trying to setup raid-1 because i'm constantly worried that my hard disk is going to fail.

i have 2 drives. one 40gb and one 80gb. so, i created a 40gb partition on my 80gb drive and i want to raid this partition with the 40gb drive. is this possible? and am i right in thinking that i can raid everything including /boot?

many thanks,
matthew horton

As encouraging as I would like to be, in this case I would not recommend you do raid 1.  It will save you from a hard drive failure, but it's not a backup replacement.  Based on my experiences software raids can be fickle, when you set one up the first thing you should do is pull a drive out and reboot - make sure it rebuilds & works.  If it fails the rebuild, get a different solution.  Generally you also want the drives to be as close to the exact same size as you can get.  Remember that with raid 1 the drive is being mirrored.  If you have a 40GB drive you're mirroring, 40GB on your 80GB drive basically becomes unusable.  

If you want to do it right, pickup an Areca ARC-1200 card or other hardware based raid solution, some motherboards have decent raid support built in even.  It will perform better, SATA is surprisingly faster than IDE, and be easier to setup than a software raid.  However, you're probably using IDE drives, I don't know of any good IDE controllers, 3Ware used to make a bunch of them, but I don't see any on newegg. Stay away from the HighPoint controllers they may work but generally they don't behave as expected.

---

