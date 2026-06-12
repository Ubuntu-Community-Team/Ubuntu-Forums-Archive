---
title: "multiple  ubuntus in grub.. how do I uninstall the other ubuntus?"
date: 2010-05-11
forum: General Help
---

### Post by user1001 on 2010-05-11
Hey 

I installed Ubuntu previously long time ago, my brother accidently done a xp recovery that doesn't do full formatting..
now I installed Ubuntu 10.04 and found numerous ubuntu installations in the grub menu...

Im setting up my Mail etc in the newly installed 10.04. I found that it knows my googlemail adress from my previouse ubuntu installations..

how can I make a fresh ubuntu installation with an xp dual boot..

I already have XP as a dual boot i don't want to touch it. just remove the other old ubuntus and install a fresh ubuntu in place of it,, so I'll just have 1 xp and 1 ubuntu option with 2 partitions...

thanks .

BTW here is a GParted Screenshot:
[http://i43.tinypic.com/2rnby9g.png]("http://i43.tinypic.com/2rnby9g.png")
It needs alot of cleaning to do..
By the way I don't have an xp cd to fix the mbr.

---

### Post by user1001 on 2010-05-11
Bump..

---

### Post by alienprdkt on 2010-05-11
These are prolly not multiple Ubuntu's but rather different Kernel versions.

It is good to keep at least one previous kernel version until you have tested out the new version with your hardware, making sure everything is running smooth and up to par, so to speak. I have had problems after kernel updates.

But if you really want to remove the previous versions.

Delete them from 

/boot/initrd.img-* 

remove all the versions you don't want

to remove from grub's bootloader list you will have to edit 

/boot/grub/menu.lst 

remove the lines corresponding to the initrd-img-* files you had removed.


Hope this helps.

---

### Post by user1001 on 2010-05-11
> **alienprdkt said:**
> These are prolly not multiple Ubuntu's but rather different Kernel versions.

It is good to keep at least one previous kernel version until you have tested out the new version with your hardware, making sure everything is running smooth and up to par, so to speak. I have had problems after kernel updates.

But if you really want to remove the previous versions.

Delete them from 

/boot/initrd.img-* 

remove all the versions you don't want

to remove from grub's bootloader list you will have to edit 

/boot/grub/menu.lst 

remove the lines corresponding to the initrd-img-* files you had removed.


Hope this helps.

thanks.. 

well When I tried going into the other options, they were completely different ubuntus.. one was kubuntu, one was ubuntu 9.10 and the one I am on is 10.04.
and the others had files on it and this one that i newly installed hasn't got anything..

so i don't know, I don't want the other ones because I want to do a fresh install in place of all of them and leave xp next to it. so basically looking at the partitions.. I would like to replace dev/sda3 with one new ubuntu 10.04 and just have XP and UBUNTU 10.04 as the options..

---

### Post by oldfred on 2010-05-11
Now may be a good time to think about a separate /home. You already have a second ext3 partition that you can use. 

If you want to use existing partitions, you have to use manual install and choose which partition is / (root) and its format. It finds swap, but you might want to delete both swaps and create one new one that is larger. And if you want a separate /home you have to choose that also. If /home has your home data you DO NOT format it. 

You of course need to have a good backup of /home as that has all your user settings. If you did many system settings they are in /etc and you may want to back them up. If you installed lots of applications you can export that list and reimport it so you have all the same apps available.

---

### Post by alienprdkt on 2010-05-11
> **user1001 said:**
> thanks.. 

well When I tried going into the other options, they were completely different ubuntus.. one was kubuntu, one was ubuntu 9.10 and the one I am on is 10.04.
and the others had files on it and this one that i newly installed hasn't got anything..

so i don't know, I don't want the other ones because I want to do a fresh install in place of all of them and leave xp next to it. so basically looking at the partitions.. I would like to replace dev/sda3 with one new ubuntu 10.04 and just have XP and UBUNTU 10.04 as the options..

Could remove them as I have stated and then remove the partitions if you have multiple ubuntu's installed or want to get rid of kubuntu by installing and using g-parted

apt-get install gparted

easy to use app to remove partitions,

then do as oldfred had suggested and backup your home directory to the old partition good for updating from clean installs then you have the option of not writing over your home directory

upon installation choose manual for the partition editor and make path to you new home directory, and don't check the box to format...

(incase you hadn't done this before) please see here:
[URL="http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide"]http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide
[/URL]

---

### Post by user1001 on 2010-05-11
> **oldfred said:**
> Now may be a good time to think about a separate /home. You already have a second ext3 partition that you can use. 

If you want to use existing partitions, you have to use manual install and choose which partition is / (root) and its format. It finds swap, but you might want to delete both swaps and create one new one that is larger. And if you want a separate /home you have to choose that also. If /home has your home data you DO NOT format it. 

You of course need to have a good backup of /home as that has all your user settings. If you did many system settings they are in /etc and you may want to back them up. If you installed lots of applications you can export that list and reimport it so you have all the same apps available.

thanks 
How do I install manually? I guess theres an option right ?
I'm doing this because previously my wireless and sound cards worked with 9.10 but not in this current version i just installed..
I'm thinking maybe i didn't really do a clean install since the mail program found my email address, and if I do a clean install it might fix everything.
but wireless + sound wasn't working with the live cd either I don't know :\

---

### Post by oldfred on 2010-05-11
Even though these show different versions, they are all similar. Choose manual install is one of the first choices.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

I did not have any problems with wireless or sound, but have seen several threads with those issues. Search or browse the forum and if you do not find anything start a new thread on each issue.

---

### Post by user1001 on 2010-05-11
> **oldfred said:**
> Even though these show different versions, they are all similar. Choose manual install is one of the first choices.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

I did not have any problems with wireless or sound, but have seen several threads with those issues. Search or browse the forum and if you do not find anything start a new thread on each issue.

Thanks, I already have a thread about my issue.. 
[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Since my network card worked out of the box with previous releases of Ubuntu, 9.10 to be specific, I don't see any reason it shouldn't work with 10.04 LTS.

---

### Post by Ichido on 2010-05-12
But if you really want to remove the previous versions.

Delete them from 

/boot/initrd.img-* 

remove all the versions you don't want

to remove from grub's bootloader list you will have to edit 

/boot/grub/menu.lst 

remove the lines corresponding to the initrd-img-* files you had removed.


I followed your instructions, but it made no change to my GRUB Menu.
What next?

---

### Post by linuxman94 on 2010-05-12
Please unmark your thread as solved, more people will see it that way.

---

### Post by oldfred on 2010-05-13
To update grub or grub2 menu's/grub.cfg:

sudo update-grub

---

### Post by user1001 on 2010-05-13
> **linuxman94 said:**
> Please unmark your thread as solved, more people will see it that way.

done :).. I did it because I sorted it out by formating the ubuntu partitions using the ubuntu installer. :)

---

