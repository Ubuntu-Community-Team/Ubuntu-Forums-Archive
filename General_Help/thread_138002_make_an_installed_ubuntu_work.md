---
title: "make an installed ubuntu work"
date: 2006-03-01
forum: General Help
---

### Post by gizmokaka on 2006-03-01
Hi everyOne,
I have a problam which goes something like this:
I have a windows machine on one HD
I installed a linux machine on another HD, but disconnected the windoes HD during the process in order not to corrupt my windows installation.
when I did this with fedora core I encountered no problam, but after I finished installing ubuntu I cant boot it up if I connect the windows HD also!
to make a long story short, if i boot linux when only the linux drive is plugged in then I have no problam. But if I boot up the system when both are atteched I cant boot linux, get error !
by the way both HD are sata !!!!!
I want to share the error with you but dont know how cause I dont know how to copy the text in the black screen
sorry I m new to linux (and computers)
appreciate your help alot 
thenks!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by frodon on 2006-03-01
I'm sure it's because both hardrive contain a boot sector. You used windows on your other hdd at the time so you used this drive to boot therefore there is a boot sector on it.
You installed ubuntu on a harddrive therefore you installed a boot sector on it, how will you computer understand 2 hdd with a boot sector for each, how can it know which hdd to boot.
So don't worry, plug your 2 hdd and boot on the ubuntu install CD, press "escap" during the process and go directly to the partition step, use the this step to remove the boot sector on your windows partition.
Then to add windows in the grub you have to choice i think, add by hand the windows partition in the grub config file or re-install the GRUB with the install CD : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by gizmokaka on 2006-03-01
Well I am kind of afraid doing so cause
I dont wanna mess my windows installation 
how exectly do I register windows to the grub?
hope u can guide me cause I am clueless

---

### Post by frodon on 2006-03-01
Don't worry you will not mess up your window partition and i will help you.

The first thing to do is to remove the boot sector on the windows partition :
1- boot on the install CD and go to the partition step, don't worry at this step you didn't change anything, and the "escap" button allow you to skip the previous steps and go directly to the partition step if you wish.
Chosse to edit manualy the partitions : 

[IMG]http://users.bigpond.net.au/hermanzone/p3/i0023op.gif[/IMG]

Then edit your windows partition and remember its name (here hda1) : 

[IMG]http://users.bigpond.net.au/hermanzone/p3/i2981op.gif[/IMG]

And here put the bootflag off : 

[IMG]http://users.bigpond.net.au/hermanzone/p3/i2982op.gif[/IMG]

Then press the finish partitioning and write changes to disk button : 

[IMG]http://users.bigpond.net.au/hermanzone/p3/i1304op.gif[/IMG]

Now reboot and you shouldn't have problems to boot on linux but you will not see your window partition in grub.

So when you're in linux use this guide to add the windows entry in your grub : [http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu](http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu)

If it don't work you may have to reinstall GRUB, so you could use the link i gave you in my first post

---

### Post by gizmokaka on 2006-03-01
Thanks man 
I cant try what you said till later
you r very nice
I will how ever sit on it as soon as I get home 
and I **will** use your help man
thanks alot again & you should know that people like you will 
expand the linux community around the world
:)

---

### Post by gizmokaka on 2006-03-01
by the way I have to point out
that I am telling the computer from where to boot
threw the bios (change seqance)
and when I did the same thing with fedora core It worked like magic 
so I still dont anderstand where the problam is
any how I will try out your suggestion.

---

### Post by frodon on 2006-03-01
You mean that you tell in BIOS with which drive you want to boot ?

I'm not sure i'm right but it's the first thing i tought when i read your post, but anyway i think we will find a solution it don't seems to be a huge problem.

---

### Post by gizmokaka on 2006-03-01
hey man I cant believe it I wrote a lot & it went down with the toilet when tried to save. any way found out (I think) what the problam is & how to solve it!
when I installed ubuntu it was the only drive connected there for was registered as sda. but when I connected the other drive and booted the system the windows drive recieved the sda because it preceeds the linux HD on motherboard channel there for linux did not find from where to boot. So all I had to do was to switch channels between the two HD's on motherboard!
so 1 problam fixed & now I need something else
I wanna dual boot linux & windows 
can you help me with that????????????????????????????????
by the way still both partitions are bootable (one on linux & 1 on windows)

---

### Post by frodon on 2006-03-02
If it works like that and fit to your need you can keep both drives bootable.

For your dual boot, try to add a windows entry in the GRUB config file : [http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu](http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu)

If it doesn't work, the quickest way to get your dual boot working is to re-install GRUB and there are several ways to do that : 
1- With the install CD : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)
2- With the live CD : [https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?)

Hope you will get all working soon ;)

---

### Post by gizmokaka on 2006-03-06
thanks it works

---

