---
title: "I need partitioning help"
date: 2012-08-04
forum: General Help
---

### Post by fbjoey on 2012-08-04
Hi,

I'm trying to install Ubuntu onto my laptop. At the moment its running windows 7 but I want to dual boot it with Ubuntu. I don't know wether I'm being very stupid or am just missing something but I don't understand how the partitioning works.

I run the liveCD/install disc and get to the partitioning section and just cannot figure our what to do. I have  4 different things I can click. /Dev/Sda, /Dev/Sda1, /Dev/Sda2, /Dev/Sda3. 

I don't know if I've given you enough information or not but please can I get some help.

Cheers
Joe

---

### Post by Dylan1473 on 2012-08-04
Are you installing from the LiveCD? You should be able to automatically set it up in such a way that it dual boots with Windows through the installer. Did you try to manually set up partitioning at some point? You could try to back up a few steps and see if an option to do it automatically comes up.

As it is it sounds like you have three partitions on your computer plus the base disk or are trying to set up three partitions. /dev/sda is the full disc, while /dev/sda1, /dev/sda2 and /dev/sda3 are all partitions. Have you ever done any partitioning on your computer in the past or installed any operating systems besides Windows?

---

### Post by fbjoey on 2012-08-04
Yer i'm installing from the liveCD. I know i should be able to set it up automatically through the installer I just don't understand what I'm ment to do once I get to the partininer section of the installer. 

I've dual booted before on a different system using gparted but it was about 3 years ago and I cant remember how I did it.

---

### Post by Dylan1473 on 2012-08-04
I meant on this computer. Did you try going back a few steps? You should get a screen looking like this:

[IMG]http://leekaelin.co.uk/downloads/TechSpot/Linux_Guides/Ubuntu_11_10/Ubuntu_11_10_Capture3a.JPG[/IMG]

except it'll have a third option for booting alongside Windows. There's no need for you to mess around directly with the partitions if you're not comfortable with that. It sounds like you clicked on the something else option.

EDIT: Were you looking to setup a partitioning scheme different than Ubuntu's default? That's fine to, but please provide more specific info about what you want if so.

---

### Post by fbjoey on 2012-08-04
yer I get that screen come up. I only have two options like the one you've shown. So I asummed I was meant to click on the Something else option. Its the screen after that that I'm stuck on.

---

### Post by Dylan1473 on 2012-08-04
Wait, it says no detected operating systems? Is your Windows install working properly?

---

### Post by fbjoey on 2012-08-04
Haha sorry. Yer its working properly, its the same as in it only has the two options not three. It doesn't say theres no operating system, its says  windows 7 is installed.

---

### Post by Dylan1473 on 2012-08-04
But it doesn't give you the option to automatically install it for dual boot? Well, what options do you get if you click something else? Maybe I'm just misremembering the order they're in.

---

### Post by fbjoey on 2012-08-04
No theres no automatic install option. When I click on something else I get a  window with the partinaning tableo /Dev/Sda, /Dev/Sda1, /Dev/Sda2 and /Dev/Sda3. It has options to add, change and formatt and to get a new partininging table but they don't allow me to click on them. At the bottom there is an install button and when I click that its comes up with the error message "No root file system is defined please correct this from the partitioning menu"

---

### Post by Dylan1473 on 2012-08-04
That's all very strange. I don't have an install disc with me to test out right now, either. Does it say anything next to any of the partitions? The previous partitioning you did was not on this machine or hard drive, right? Only Windows has ever previously been installed on this computer?

The root partition is probably /dev/sda by the way. You shouldn't have to do this manually, though....

---

### Post by fbjoey on 2012-08-04
No, its only ever had windows 7 on it. It says NTFS next to /dev/Sda1 and /dev/sda2. I cant remember what it says next to 3. Yer it would make sense that /dev/sda is the root partition, 1,2 and 3 all apear underneath if slightly in, as if there "sub-partitions".

---

### Post by Dylan1473 on 2012-08-04
Well, I think Windows sometimes uses 2 or 3 partitions. One recovery, one for the actual install, and I forget what the third one is. At any rate you probably shouldn't delete any of those. Well, you could try restarting the installer and hoping it works next time, but otherwise we'll have to do this manually. 

Back up anything important you have on Windows on an external hard drive or a flash drive or something - think documents especially and anything else you really don't want to lose. The critically important stuff shouldn't take up too much space, it tends to be videos, games, music, and other big applications that take up the most space. You probably won't lose it, but just in case. I'm gonna edit this or post back in a bit with an explanation on how to manually partition the drive. It's not *too too* hard to do as long as you follow instructions, understanding what it all means gets a bit more complicated but it's not mandatory.

---

### Post by fbjoey on 2012-08-04
I've tried installing restarting it a few times and it always comes up with the same thing.

Yer it would be great if you could post some instuctions for a manual install. I'll start backing up my stuff now. 

Cheers for the help

---

### Post by Dylan1473 on 2012-08-04
First thing's first: are the Windows partitions taking up your entire  drive? I'd assume so. You'll need to resize one of them (the biggest  one, it'll be formatted as NTFS and *probably* be /dev/sda3) to allow some space for Ubuntu. That's probably why you can't  create new partitions right now. You can probably resize it by right clicking on it and selecting a menu option that looks appropriate (it might be properties or something or it might literally say resize, I don't remember). Careful not to shrink it so much that  it's smaller than the space used or you'll lose some files. You'll also  probably want to leave some space there for Windows to continue using.  Unless you're planning to fully migrate to Ubuntu - storing games and  other big applications and stuff on there - you won't need a huge amount  of space for it. 20 to 30 gigs should be plenty (a minimum of 5 is  recommended in the system requirements), though you can of course go way more or even a bit less if  you so wish, depending on how you want to use it.

Now you need to make a new partition, and make it a logical/extended  partition. Let it take up the rest of your drive unless you want to  reserve space for additional operating systems or to increase the size  of partitions as you find appropriate later (that might be a good idea if you choose to do more than root, swap, and maybe boot partitions). After this, you're going to  add some sub partitions to that logical partition. Here's an  explanation of what you can choose to add, only a few are technically  absolutely necessary.

1) The root partition. This one is mandatory - it's basically the entirety of your actual Linux system. You can run fine with just this, but you should probably at least have swap as well. To make this, click the new partition thing, choose ext4 as the file system type if it asks you, set the space as you think appropriate (you may be able to make do with as little as 5 gigs here, some people would recommend as much as 20 - this is where the files for most of your installed programs will actually go, but that's not as horrific a prospect as it is with Windows since you won't be installing tons of massive game files that way). The mountpoint of this one is just the /.

2) The swap partition. This isn't strictly mandatory but Ubuntu uses it by default and I really, really, really recommend you make use of it. You may be able to make do with just 1GB. You probably should make it equivalent to your RAM. Many people would recommend you make it double your RAM, and you can do this if you want to be safe and have lots of hard disk space to spare. It should be greater than or equivalent to your RAM if you want to be able to hibernate your computer. If this one even has a mountpoint it'll be labelled as swap, but I don't think you have to choose one. It's formatted as linux swap for the filesystem.

3) A boot partition. This one is optional but I like to keep it around just in case. It can be useful if something goes terribly wrong for recovery purposes, among other things. For the relatively small size it requires (you can do 100-200MB, I'd recommend 200MB since hard disk space is pretty cheap these days) it's well worth it. I'm not sure but I don't think Ubuntu uses this by default. The mount point of this one is /boot. It can be formatted as ext2.

4) A home partition. This one is optional and I don't personally use it. There are excellent reasons you might choose to though. This makes it a lot easier to transfer your home directory (with most of your personal files and many configuration files) from installation to installation. The only thing is that you have to kind of balance your space between this and root properly since you have to choose how much to allocate to each if you use separate partitions. If you're not sure it's possible to move /home in other ways or migrate it to other partitions later. This one is mounted at /home and should be assigned most of the space you don't give to root or wish to leave reserved. Like root, this should be formatted as ext4.

Those are the typical ones - there are others but they tend not to be used all that much for desktop computers, especially by new users. Anyway, set up the partitions as you like and then post what you've got before you actually commit the changes.

EDIT: If you have any questions of course feel free to ask. You're not supposed to have to do this.

---

### Post by oldfred on 2012-08-04
That usually is the screen you get when you have all 4 primary partitions used.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by fbjoey on 2012-08-04
Yer I just failed at the first hurdle. I cant figure out how to resize /dev/sda3. Its gives me change, delete, revert, theres no right click or preferences. Theres no options to resize with the change options window either.
I'll try change it in Windows like oldfred suggested.

---

### Post by Dylan1473 on 2012-08-04
That's a good idea. I didn't have problems as a result of resizing from the Ubuntu installer but I've often heard that you can.

EDIT: Another good point from oldfred - I'm assuming you still have your Windows install disc or a Windows repair disc? I've had minor issues before where Windows stopped working and required the use of a repair disc as a result of messing around with partitions. It wasn't in the installer, but it's happened. It's possible to get one from other sources legally I think, but you'd probably be better off making your own if you don't have one.

---

### Post by fbjoey on 2012-08-04
I resized the partition in windows. I'm sure my windows repair disc is about somewhere. Its my Mums old laptop and she always keeps everything. But anyway I didn't have to install it manualy. Once I resized the partition in windows and then restarted with the Ubuntu install disc it gave me the option to install auotmatically alongside Windows. Way!!!!

Cheers for all the help. Promlem solved!

---

### Post by Dylan1473 on 2012-08-04
Oh weird, it should have been able to resize it automatically. I wonder if that was taken out in 12.04 due to problems with resizing Windows partitions? Well, glad you got it fixed, enjoy Ubuntu.

---

### Post by fbjoey on 2012-08-04
I'm enjoying it already. Its so much faster than Windows!!!

---

