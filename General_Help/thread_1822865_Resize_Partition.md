---
title: "Resize Partition"
date: 2011-08-11
forum: General Help
---

### Post by NM5TF on 2011-08-11
when I first installed Ubuntu in 2008 I used the 32 bit version....

I recently installed the 64 bit version to take advantage of my
dual-core hardware, but I kept the 32 bit version as a dual-boot
system...just to see if all my apps were supported & worked under
64 bit....they seem to work fine...

Now I find that I am running out of space in the 64 bit version..
I would like to resize, or entirely remove, the 32 bit version &
allocate all disk space to the 64 bit OS....

I installed GParted & started to do that, but get a warning message 
saying that the 32 bit version is flagged as "boot"....

If I proceed, will it erase the boot partition & lose the ability to
use my PC???

Forgive the noob question & long post, but I am a hardware guy & not
a software guru...:confused:

---

### Post by ajgreeny on 2011-08-11
You will need to use a live CD and run gparted to do what you want to, but first it would be good to know which of the two systems is supplying grub that is currently being used at boot.

You need to make sure that the 64bit system has the active, current grub, so boot to your 64 bit system and then run ```
sudo grub-install /dev/sda
``` assuming sda is the disk with ubuntu on it; if not change the device name.  That will make sure your 64bit system has the active grub.

Now using the live CD, you can delete the 32bit OS root partition and extend the 64bit partition, or just make a new partition if the two were not side by side, but make sure you backup any hidden config files that may be useful later on.  You can totally ignore the boot flag warning as a boot flag is not needed for linux;  all that is needed is grub in the MBR of the first boot device, which you have already dealt with.

---

### Post by NM5TF on 2011-08-11
> **ajgreeny said:**
> 

Now using the live CD, you can delete the 32bit OS root partition and extend the 64bit partition, or just make a new partition if the two were not side by side, but make sure you backup any hidden config files that may be useful later on.  You can totally ignore the boot flag warning as a boot flag is not needed for linux;  all that is needed is grub in the MBR of the first boot device, which you have already dealt with.


okay....I did all that & deleted the 32 bit partition which gave me 179.91GB of unallocated space....:P

my only gparted option for the 179.91GB of space is to create a new partition...:confused:

when I try to resize the 64 bit partition, it only wants to let me make it
smaller....:(

how can I reallocate the 179.91GB to the 64 bit partition???:confused:

---

### Post by ajgreeny on 2011-08-11
Can you show a screenshot of gparted.  That may help to figure out what is going on and why you can't enlarge the 64bit partition.  It is possible that the deleted partition, now free space, is within an extended partition alongside your swap, but let's see what the screenshot tells us.

I will have to leave it to another to answer further, as I'm going to be out of contact for a week, I expect, from later tomorrow, but I'll look when I get a chance to see if anyone else has managed to sort the problem for you.

---

### Post by NM5TF on 2011-08-11
> **ajgreeny said:**
> Can you show a screenshot of gparted.  That may help to figure out what is going on and why you can't enlarge the 64bit partition.  It is possible that the deleted partition, now free space, is within an extended partition alongside your swap, but let's see what the screenshot tells us.

I will have to leave it to another to answer further, as I'm going to be out of contact for a week, I expect, from later tomorrow, but I'll look when I get a chance to see if anyone else has managed to sort the problem for you.

OK, here is screenshot of gparted...

---

### Post by ravij96 on 2011-08-11
Hey I just finished doing what you want to do. You have to go into the Ubuntu LiveCD and right click ont he extended part and resize it to include the unallocated space. You then do the same thing with you ubuntu partition. So you would extend sda2 to take up the unallocated space. Then the unallocated space will be right above sda6. You then extend sda6 to take up the unallocated space. WARNING: this will take awhile i only did this with 50gb and it took an hour.

---

### Post by NM5TF on 2011-08-11
I found another thread where someone was wanting to do the same thing
as I want....someone solved it for him...I will try the same fix to see
if it works for me & report back....if it fixes it, I will mark my thread
as solved....

thread here:

[http://ubuntuforums.org/showthread.php?t=1823087&highlight=resize+partition](http://ubuntuforums.org/showthread.php?t=1823087&highlight=resize+partition)

---

### Post by ravij96 on 2011-08-11
Ironically that was my thread x) good to see you solved it.

---

### Post by NM5TF on 2011-08-11
> **ravij96 said:**
> Ironically that was my thread x) good to see you solved it.

not quite....that fix doesn't work for me, don't know why....

here is new screenshot of gparted:

---

### Post by niko123456 on 2011-08-11
your file system looks a little strange. bits missing and more than one swap partition etc..

I actually resized a partition using gparted just the other day (using a Fedora live cd). It copies your data to the left and then resizes to the right. 

..so it is possible. i'd make sure you didn't have any of the drives mounted and you were running gparted as root.

edit: I see now. you want to resize sda2 first.

---

### Post by oldfred on 2011-08-11
You can only use gparted on unmounted partitions. Best to run from liveCD and even then liveCDs often mount swap to speed things up so you have to click on swap and swap off.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

A few computers have to have a boot flag on a primary partition. Grub does not use boot flag but for those systems you still have to create one. This is known for some Intel motherboards, not sure about others. If you resize your extended partition to include all of the unallocated you will only have the extended partition as a primary.

Have you thought about a separate /home? You can create a new partition and move all of /home to that partition.

Three essentially identical ways, using different copy commands.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by NM5TF on 2011-08-11
> **niko123456 said:**
> your file system looks a little strange. bits missing and more than one swap partition etc..

I actually resized a partition using gparted just the other day (using a Fedora live cd). It copies your data to the left and then resizes to the right. 

..so it is possible. i'd make sure you didn't have any of the drives mounted and you were running gparted as root.

edit: I see now. you want to resize sda2 first.

I will install live cd & try to resize sda2...will report back...

---

### Post by NM5TF on 2011-08-11
thanx 'oldfred" for the tip on the swap partitions...the secret
was turning the swap off...that allowed me to resize sda2...then
I was able to resize sda6 to the full unallocated 179.91GB...:p

this thread is now solved:P

---

### Post by brolin_1911a1 on 2011-08-12
this is just a blind guess, not seeing your system or partitioning scheme, but....

Have you tried opening Synaptic and using linux-image as a search term?

I believe that will show you all of the installed linux kernels on your system.  Select the older ones that are installed and do a complete uninstall of them, leaving just the newest installed.  I recently did that on my 32-bit machine when I upgraded to Natty Narwhal from Maverick Meerkat.  Then, after rebooting has shown you're still good, run computer janitor.

---

### Post by Connyank on 2011-08-13
I don't mean to hijack this thread but my question is on topic and quite simple for someone that has their head wrapped around the issue - mounting and Home.

I just had to reinstall lucid due to an incredibly stupid move (aptitude --keep-all).  Been using Ubuntu since 8,04 and have never used a separate /Home partition.
This time, thought it may be a good idea so created one upon the install.
On startup, lucid went ahead and created a /home folder in the extended partition, ignoring the /Home partition.

So I'm wondering - why didn't the install pick /Home up (could it have been the capital h?)  I mounted at /Home and am not sure if that is correct but I never could grok mount .  What would be the simplest way to force its use?

Thanks and I return you to your regular programming...

jg

---

### Post by oldfred on 2011-08-13
None of the installs automatically use /home. You have to use manual install or Something Else in Natty and choose which partition is /home. Linux is case sensitive where windows is not so /Home would not be a /home partition in Ubuntu and would be seen as just another mount point.

You probably just need to add it to fstab. You may now have some new settings in the new home it created that you want to copy over.

You need to review the way to copy /home to a new partition and mostly just have to do the last part where you add the new partition into fstab.

These three are essentially the same. Just using different copy commands, which you may or may not need.
# MoveHome.txt
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Connyank on 2011-08-14
> **oldfred said:**
> None of the installs automatically use /home. You have to use manual install or Something Else in Natty and choose which partition is /home. Linux is case sensitive where windows is not so /Home would not be a /home partition in Ubuntu and would be seen as just another mount point.

Ok, so if I made it /home things would have been different....hmmm


You probably just need to add it to fstab. You may now have some new settings in the new home it created that you want to copy over.

yup

You need to review the way to copy /home to a new partition and mostly just have to do the last part where you add the new partition into fstab.

These three are essentially the same. Just using different copy commands, which you may or may not need.
# MoveHome.txt
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Thanks for that - I'll look into it and get back.

jg

---

