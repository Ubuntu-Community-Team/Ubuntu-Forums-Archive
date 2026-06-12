---
title: "Tri-boot (10.04, 7, XP) ... 7 fails to boot"
date: 2012-01-04
forum: General Help
---

### Post by Cakewalking on 2012-01-04
I had Ubuntu 10.04 LTS and Windows 7 Home Premium dual-booting fine for the past year, but an application that I really need does not work well under Windows 7, so I made another partition and installed Windows XP Professional onto it.  After installing Windows XP, I re-installed GRUB2.  A problem I had was that Windows XP didn't get detected by GRUB2 (even after update-grub), and Windows 7 Loader boots to Windows XP.  I have modified grub.cfg and created a Windows XP Professional entry under the probe area and everything works fine with on the XP part, but I can't seem to get 7 booting?  Can anyone please help me out?

---

### Post by Cakewalking on 2012-01-04
Bump. Please guys.

---

### Post by imachavel on 2012-01-04
dude I have had this grub problem with windows and linux dual booting more times then I can explain. Why don't you take a gander at a few pieces of a previous thread I had going, but it probably won't help you much:

imachavel:

now before you guys go deep into a tale about how I  should use google, I've been using google extensively. I can't find the  answer I'm looking for, fdisk seems to want to format a partition more  then anything else, although fdisk -l seems to give good results for  information.

here i my issue, when I try and dual boot, windows  xp with ntfs isn't found. when I try and load it, I get this error:  device format "/dev/sda, msdos1" invalid: must be (f|h)dn, with o <= n  c 128

so in ubuntu it was recommended I try this from an online article:
```

sudo mount /dev/sdb1 /disk1 

but this is the result I get:

Mount  is denied because the NTFS volume is already exclusively opened. The  volume may be already mounted, or another software may use it which  could be identified for example by the help of the 'fuser' command.

also, just to be clear, /dev/sdb1 is the ntfs windows partition, not /dev/sda

now in windows, setting this partition as active is as simple as using these tools:

diskpart
list disk
select disk
list partition
select partition
active

why  is this so complex in linux?? would it not be as simple? the weird  thing is, windows was installed first, and then when I installed linux  under dual boot, at first linux stopped showing up, when I marked this  partition as active, it worked, but now I can only load into ubuntu, and  not windows. so it's the opposite now [IMG]http://www.shroomery.org/forums/images/smileys/facepalm.gif[/IMG]

would anyone like the results of fdisk -l? THANKS 



dawks said:

 [COLOR=#008A17]>using windows XP
>2011[/COLOR]

[INDENT]Quote:
***imachavel said:***
would anyone like the results of fdisk -l? THANKS

[/INDENT]

It wouldn't hurt.

You're MBR is located on the first part of your first disk (/dev/sda).

What *I* like to do, is to create a boot partition as the first primary partition on the first disk.

Something like:

Code:Device		Boot		Id		System
/dev/sda1	*		83		Linux (bootloader partition)
/dev/sda2			82		Swap
/dev/sda3			83		Linux (root/filesystem partition)



Then you'd need to tell the grub config (/boot/grub/grub.conf) to boot from it, so it would be like:

Code:title Ubanto
root (hd0,0)
kernel /boot/<kernel name> root=/dev/sda3

The you'd add a windows XP entry to grub (/dev/sdb1 is called hd1,0 in grub):
Code:Title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1


And that should boot XP.

Edit:
Disregard my pervious babble and just post your *fdisk -l* output and your [I]grub.conf



imachavel said:


[/I]fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbcd9bcd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       28683   230396166    7  HPFS/NTFS
/dev/sda2   *       44619       60802   129989632   83  Linux
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

grub.conf:

danel@danel-Dimension-4700:~$ sudo grub.conf
sudo: grub.conf: command not found

I didn't get much help on that last one huh? my mistake, the fdisk -l help you out any?? 


dawks said:


Many apologies for the delay my friend.

Alrighty, let's do this.

Step 1:
Let's find out what /dev/sda1 is. 

We'll do this by mounting that partition and seeing what files it contains.

To do this type:

Code:sudo su
mkdir /mnt/devsda1mntpnt
mount /dev/sda1 /mnt/devsda1mntpnt

[COLOR=#FF0004]**If** it spits you an error about something being mounted already type this:

Code:mount

And paste me the result.[/COLOR]

Otherwise type:
Code:cd /mnt/devsda1mntpnt
ls

And paste me the result.

Step 2:

Let's try automatically reconfiguring grub2.

Type:
Code:sudo su
grub-install /dev/sda
update-grub
reboot

Now see how you go, can you boot into Windows or Ubuntu now? give it a shot and see what happens. 

Step 3:

Grub2  is nasty complex piece of software that I'm for the moment unfamiliar  with. Unfortunately ubuntu packages this silly bootloader with it by  default (change for the sake of change I guess [IMG]http://www.shroomery.org/forums/images/smileys/shrug.gif[/IMG]).

Let's remove that nasty grub2 and replace is with a more reliable, more helpful legacy grub.

Type:
Code:sudo su
apt-get purge grub2 grub-pc


It'll ask you if you want to remove and bla bla, hit yes.

Now that grub2 is gone, let's install grub.

Type:
Code:apt-get install grub
mkdir /boot/grub
update-grub
grub-install /dev/sda
update-grub

It'll ask you if you want '/boot/grub/menu.lst' generated you. [COLOR=#FF0004]TYPE **Y**[/COLOR] (default is N so you MUST type [COLOR=#FF0004]**Y**[/COLOR] MUST MUST).

Did anything go wrong? if you got any errors at all during this part paste them too me.

Okay now reboot (type [COLOR=#FF0004]reboot[/COLOR] to reboot).

Can you boot into windows? does it work now? If not, go to the next part.

Step 4:

Assuming  you've gotten this far and you can still boot into Ubuntu but not  windows than that's excellent. What you need you to do is type: 

Code:cat /boot/grub/menu.lst


And paste me the output. We will take it from here.


Do [COLOR=#FF00C3]Step 1[/COLOR] and then [COLOR=#FF00C3]Step 2[/COLOR].  If at any point you fix it between step 2 and 4 then congratulations,  otherwise we should be able to work out what's up after you complete up  to step 4. 



cutless said:

 Boot into your Linux distro or a live cd, open GParted, right click on  your Windows NTFS partition, choose manage flags, and check boot. Not  sure if it'll automatically show up in GRUB on restart, I doubt it  though. So you may have to re-add the Windows XP option or just  completely reinstall GRUB. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 
    
   





Anyway let's not go any further the thread was 3 pages, no answer was found. I'd think maybe it be time for the ubuntu development team to develop a better grub and a better llegacy grub. But then that sounds like a lot of code, and I have no time or resources to test that code, or to explain why it should work better or not. I know very little about the linux grub, very little. From what I know, windows doesn't like to play nice. It wants it's own master boot record, it's own grub loader, etc. But then windows is the first thing that won't boot. Anyway, if the ubuntu moderator asks me to write some grub code, I'd have to figure out how to write it. Since I don't, what can I do. Sorry man I just don't even slightly know what to tell you :popcorn:
```

---

### Post by imachavel on 2012-01-04
> **Cakewalking said:**
> Bump. Please guys.

btw, I'd recommend posting this:

sudo su
[sudo] password for danel: 
root@danel-Dimension-4700:/home/danel# mkdir /mnt/devsda1mntpnt
root@danel-Dimension-4700:/home/danel# mount /dev/sda1 /mnt/devsda1mntpnt


meaning I'd try using these commands:

>sudo su
>mkdir /mtn/devsda1mntpnt
>mount /dev/sda1 /mnt/devsda1mntpnt

although obviously they didn't help me, I upgraded from natty narwhal to onereic ocelot I believe. I'm not sure why those commands for me returned no results. I'd assume we are using the same shell??

---

### Post by coffeecat on 2012-01-05
@**imachavel**, please do not post a great wall of text without some attempt at formatting and use of BBCode. No one is likely to read your post #3 the way you presented it. I have enclosed a portion of it in code tags so that it is slightly more presentable to people wanting to review the whole thread.

@**Cakewalking**, I'll close this thread as I see you have started a new one here:

[http://ubuntuforums.org/showthread.php?t=1904546](http://ubuntuforums.org/showthread.php?t=1904546)

---

