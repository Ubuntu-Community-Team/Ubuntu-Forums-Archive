---
title: "Please Help ! Error: out of disk -grub rescue &gt;"
date: 2012-02-28
forum: General Help
---

### Post by Jim Bovey8t8 on 2012-02-28
Please Help !
I have been struggling with this situation for the past week and am at my wits end !!!

I am using an old computer that previously worked fine with ubuntu:

Motherboard= MSI KT4 Ultra 
chipset= kt400(a)/600
Memory=2GB
CPU= AMD 2200+
Video Card= AGP


Hard drive was 2tb hard drive from Western Digital
Model: caviar green wd20ears 64mb cache
Sata 2

It worked fine for months on this computer but was using an updated version (11.10)
which i didn't like so i formatted it and used the drive for something else.

So I then recently bought a new drive for this computer :

2tb hard drive from Western Digital
Model: caviar green wd20earx 64mb cache

The difference is this drive is sata 3

Everytime i install ubuntu 10.04 on it,
the installation goes well if i skip the RAID setup from the BIOS 
What I mean by that is that Ubuntu cannot install on my new drive if my new drive is part of a RAID setup as requested by the BIOS.

But then if i reboot, my BIOS cannot see my drive until i tell the BIOS to use it in a RAID setup.

Weird.

So i setup the new drive as part of a single RAID (with a thing called FastBuild Utility). ,
I reboot and i get this:

Error: out of disk
grub rescue >

So after searching the net i foud the:

-ubuntu 10.04 alternate install
which you can find here:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

and the
-ubuntu boot repair 
which you can find here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


With the ubuntu boot repair i made a diagnosis which you can find here:
[http://paste.ubuntu.com/861294/](http://paste.ubuntu.com/861294/)

I usually solve my problems myself but this time i would greatly appreciate a little help from the Ubuntu Community.
I have used and recommended Ubuntu to my friends and even installed it on a friend's laptop, she loved it !

Thanks in advance !

---

### Post by oldfred on 2012-02-29
There was a bug which I do not know if they have fixed where grub does not work in very large / (root) partitions (over 500GB?). I normally suggest 25GB or so for / so never have a problem.

You can relatively quick test by using gparted to shrink / to a much smaller partition.

You then either can reinstall, move /home to a new partition or just create new data partition(s) for data you might normally have in /home.

New users I typically suggest the separate /home. If dual booting with Windows then in addition a separate NTFS partition for shared data.

And more advanced is to leave /home in /, but have a data partition for all data like Documents, Music etc and mount in fstab and link or use bind to make folder in /home look "normal", but actually be in the data partition.

---

### Post by Jim Bovey8t8 on 2012-02-29
Hi Oldfred :D and many thanks for taking the time to help me with my Ubuntu problem.

I downloaded gparted, made a small 25 gb partition as you suggested, then installed Ubuntu 10.04

When i rebooted i got a black screen with the message "no boot".

So like i did before i defined a RAID array in the bios even though i didn't need to at first with gparted and the ubuntu installation cd. 

At first i don't need to define a raid array, both gparted and ubuntu see my drive.
But after the installation if i don't define a RAID array i can't make any progress.
The RAID array is 1+0 stripe and is functionnal.

Now that i defined a RAID array, i rebooted and got a grub prompt.
So with that i did a little google search and found this page:
[http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/](http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/)

The included picture looked exactly like my screen with the grub prompt.
So i then followed the suggested procedure and got my ubuntu 10.04 alternate install disk and did a 
"repair broken system".
That didn't work.

Then i used my Boot-repair-disk that i mentionned above to try to reinstall and update grub.
After the operation, the Boot-repair-disk software told me that  my boot was successfully repaired.
This is the link to the end diagnosis:
[http://paste.ubuntu.com/862867/](http://paste.ubuntu.com/862867/)

I then rebooted and this is the message i got:

error:atapi read error
grub rescue >

What is going on please ?

---

### Post by imachavel on 2012-02-29
[http://ezinearticles.com/?Troubleshooting-Atapi-Sys-Blue-Screen-of-Death---How-to-Fix-Atapi-Sys-Error-Safely&id=5050802](http://ezinearticles.com/?Troubleshooting-Atapi-Sys-Blue-Screen-of-Death---How-to-Fix-Atapi-Sys-Error-Safely&id=5050802)

Seems the root files are corrupted. Let me ask you something, when trying to install with a raid controller, do you have matching drives, e.g. 1 terabyte each? Are you mirroring? You seem to be rather good at troubleshooting, my question is, you have narrowed it to a grub issue. So you 2 OSes going on? Immwondering if your raid controller is bad. My guess is you seeming much brighter then me, you have all your files backed up. Have you tried installing the OS on each partition on each disk separately? Without raid? It's a shot in the dark, but it seems a good trouble shooting step. I cant tell if raid OS install worked and then grub failed, or if raid OS install ever worked. Maybe you should replace your raid controller.

---

### Post by Jim Bovey8t8 on 2012-02-29
Hi Imachavel and thanks for your reply and kind words :).

I have only one drive in this computer, so i am not mirroring.
There is no raid controller card.

This is an old motherboard with 2 SATA connections from when the SATA drives began appearing many years ago.
It has a RAID controlling software integrated with the BIOS at boot.
You choose it by pressing CTRL+F and then navigate the options.
If i don't use it i can't boot the drive.
Even though in order to install Ubuntu i have to avoid it or i can't make the installation.

The computer worked fine for months with an 11.04 ubuntu installation, but then it started having a little trouble booting in recent months.
Showing the list of previous Ubuntu updates instead of the login screen.
I had to use the Boot-repair-disk once or twice to fix it successfully.

So i am starting to suspect maybe some part has slowly failed on the board.
Maybe the part that controls the sata connections.
But then how come i can still see the sata drive when i use the install disk and the boot-repair disk ? 

Before i buy a new motherboard i need to know if it it is going to make any difference.

Also since this is a new SATA 3 hard drive, it could be that this old motherboard is having problems with it even though SATA 3 is backwards-compatible.

I'll make a test with a SATA 2 drive soon.

Also:

Update:
After making many repair tries with the Boot-repair-disk, i now see the Ubuntu version listed correctly at boot on a black screen along with the memtest and a troubleshooting Ubuntu version.
But if i choose the Ubuntu i now get this message:

Kernel Panic
Not syncing:
VFS: unable to mount root.

I got this message before so i'm back at square one.

Bye for now and thanks again.

Jim.

---

### Post by oldfred on 2012-03-01
I do not know RAID, but it does write hidden meta-data that will interfere with normal installs. 

Some old BIOS could only boot from the first 137GB of a hard drive, so either the entire / (root) or a separate /boot fully inside the 137GB limit would work.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

---

### Post by Jim Bovey8t8 on 2012-03-15
Update...

Victory !!!  :p:guitar:):P

Tank you Oldfred your solution did the trick !
I booted with a USB key with Ubuntu 10.04 LTS on it and copy-pasted the 2 commands you gave me in a console:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

After that i was able to install Ubuntu on the drive.
Apparently my old motherboard installed Raid files on the drive which prevented installing Ubuntu and even formatting.

In the meantime though i got myself a new motherboard thinking that my old motherboard was the problem.
It wasn't because even with the new motherboard the problem was still there.
It was those raid files on the SATA drive that were preventing any installation and the two commands you gave me were finally able to remove those files.

Today i am not using Ubuntu 10.04 though as i wanted at first because my new motherboard is a CPU/VGA combo and the drivers ATI gives us for Ubuntu are really bad.

So i finally installed Ubuntu 11.10 with the FGLRX drivers and things are okay now.

So thanks again oldfred and everybody, i hope this thread will eventually help someone else with the same problem and i am going to mark this situation as having been solved.

---

### Post by oldfred on 2012-03-15
Glad that worked. :)

---

