---
title: "Fixing fstab or others? .. After removing swap partition to reconfigure partition"
date: 2011-09-17
forum: General Help
---

### Post by just_ken_here on 2011-09-17
Hello

I had this partition initially

[IMG]http://i1130.photobucket.com/albums/m527/kendy_loves/Partitions/Screenshot--dev-sda-GParted.png[/IMG]

sda1 - My first install of Kubuntu 9.04. Upgraded to 9.10 -- Broke it somewhat. So I shrinked the drive as you can see.

sda2 - Extended ....of 1.91 GIB. 
contains a single swap of the whole Extended drive :P - that sda5

sda3 - My current OS Ubuntu 10.10 running.

===== Of course, this is a bad setting with extended of 1.91 GB at SDA2 --
So I wanted to remove the SDA2 and redo my swap
I did : 
$ swapoff -a
then deleted SDA5 and SDA2 via Gparted
[IMG]http://i1130.photobucket.com/albums/m527/kendy_loves/Partitions/Screenshot--dev-sda-GParted-.png[/IMG]
then
[IMG]http://i1130.photobucket.com/albums/m527/kendy_loves/Partitions/Screenshot--dev-sda-GParted-1.png[/IMG]

Now. After I reboot, the OS complained about unable to mount the UUID of SDA5 the old swap.
I checked /etc/fstab:
[COLOR=Sienna][COLOR=DarkRed]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e500198d-5d15-45ed-95e6-35e53c4499b0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c0aa9271-241a-454d-a913-070caa7db66f none            swap    sw              0       0

[COLOR=Black]I believe this is still the same as the old fstab before the removal of the Extended.

-------------------------------------
Can Anyone tell me how to fix this problem (fix the linux auto mount of the removed swap)..
and anything to Let my OS know that this SDA2 and SDA5 has been removed for-ever . No longer exist..
-------------------------------------
And say that I create another swap. How can I set the OS to automatically recognize the new SWAP.

Thanks a lot for all your helps :)

[/COLOR][/COLOR]
[/COLOR]

---

### Post by oldfred on 2011-09-17
You can just comment it out with the # hash or pound sign or whatever it is called. Then when you create a new swap find the new UUID can replace the UUID with the new updated one and remove the #.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
To find uuids:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

Because you have lots of unallocated, you need to put a lot of that into an extended partition so you can make multiple logical partitions, otherwise you will run out of primary partitions.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

