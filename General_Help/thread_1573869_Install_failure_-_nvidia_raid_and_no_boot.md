---
title: "Install failure - nvidia raid and no boot"
date: 2010-09-13
forum: General Help
---

### Post by LorenG on 2010-09-13
Hello,
on my pc, that was running WinXP, I thought of installing Ubuntu.
(I did install linux already a few times in the past years and use it on another couple of pcs)
But something went wrong. This machine has 2 x 200MB maxtor drives, in raid 0 configuration, supported by the motherboard Nvidia chipset, and working well in Windows. When ran the live Ubuntu 10.04 cd, gparted was not able to access the drives in raid configuration, until I installed the mdadm and kpartx packages then the existing data became visible. So after that initial moment I thought all was ok and proceeded to install Lucid on the machine, dual booting with Windows. I did partition manually so that in my 400GB raid drive there is an 80GB NTFS partition with WinXP, a 90GB extended partition for Linux Ext4 and Swap and then a last NTFS 200GB partition for data.
All went well, but now on restarting the computer nothing happens, nothing loads, Grub is not showing, and it looks like I cannot launch Linux nor Windows.
All the data from WinXP and the Ubuntu installation seems to be on the disks but the pc is just not booting.
I suppose the problem is with the raid configuration that is not handled properly during the installation, but is there anything that I can do now, apart from reinstalling Windows Xp or installing Ubuntu in a non raid configuration?
Thanks if you can help
Regards

---

### Post by ronparent on 2010-09-13
Raid is usually a problem with a 10.04 install. Typically installation of the grub 2 boot loader will fail. It is easy enough to fix if you can follow the instructions in this: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

If you need more help, go to this site: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)
Download the Boot Info Script, run it, and post the results here. This will give us enough information to be able to give explicit instruction. Good luck.

---

### Post by LorenG on 2010-09-14
many thanks for your reply ronparent,
in the meanwhile, in an attempt to recover access to, at least, WinXP, I have installed a version of Mandriva 2010 Spring, that for some reason managed to install a bootloader.
So at present at start up I can select Windows and launch it, but still cannot load Mandriva (message says something like it cannot find the partition) nor Ubuntu (which is not even listed in the Grub(?) menu). So slightly better situation in terms of being able to access my old WinXP partition again, but not sure now if the Mandriva install might have complicated things a bit more. 
Thanks again also for the links it looks like I will have some reading to do :D

---

### Post by ronparent on 2010-09-14
Not necessarily more complicated. Just reinstall grub to the raid partition containing your 10.04 install per method 1 in the 1st reference I gave you. To be more explicit I would need to see the results from running the boot info script (2nd reference). Just remember you mount the partition with the Ubuntu install and install the boot loader to the overall raid array by name. Hint: look in /dev/mapper/. The raid array is the first name (following control) and all of the following names are the raid partitions.

---

### Post by LorenG on 2010-09-14
Hello, and many thanks again for your reply,
I am reading the Grub2 documentation but in case you could and wanted to give some more specific advice, here attached is the .txt result from the boot_info script launched within a live CD session. :-\"...

---

### Post by LorenG on 2010-09-14
.. ok I have tried to follow the instructions and to reinstall Grub for the Ubuntu partition.. did not completely work, and although now I am not presented with a bootloader anymore (the Mandriva one), there is a prompt saying "grub rescue>"..
Any suggestions on where to go from here?

---

### Post by ronparent on 2010-09-14
If you used method 1 your commands in a live cd terminal would have looked like this:

> sudo mount /dev/mapper/nvidia_fagijdii5 /mnt

This would have mounted the partition you installed to to your live session /.

Then:

> sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_fagijdii

This would have written, among other things, the boot loader to that section of the raid root (/dev/mapper/nvidia_fagijdii). Good luck.:)

Although the computer should be bootable to the install in partition #5, the mandriva menu entries may have to be rewritten to boot any mandriva installs. One of the other threads I posted to encountered this (I'll try to locate it).

Edit: [http://ubuntuforums.org/showthread.php?t=1571210&highlight=raid](http://ubuntuforums.org/showthread.php?t=1571210&highlight=raid)

---

### Post by LorenG on 2010-09-15
thanks, it looks exactly like what I did..
here it is (I took note of the screen):
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_fagijdii5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_fagijdii
You have a memory leak (not released memory pool):
 [0x96e0808]
You have a memory leak (not released memory pool):
 [0x8ab7808]
You have a memory leak (not released memory pool):
 [0x8db0808]
You have a memory leak (not released memory pool):
 [0x976b808]
You have a memory leak (not released memory pool):
 [0x8d35808]
You have a memory leak (not released memory pool):
 [0x83e0820]
Installation finished. No error reported.
ubuntu@ubuntu:~$ 
```

then on reboot I got an error message:
"error: no such device"  followed by a long identifier
and the grub rescue prompt
also is the memory leak message something to worry about?

---

### Post by LorenG on 2010-09-15
update:

reading other posts I tried the following:

> Mount your partition
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
dpkg-reconfigure grub-pc
Then I followed what was asked me on this new screen. I didn't change anything in it (except that I choose my raid in the list)

Rebooted but still same error: no such device
grub rescue>

.....

---

### Post by ronparent on 2010-09-15
It is beginning to look like raid behavior on 10.10 is in transition. I haven't seen your error but I am willing to bet the long identifier is a raid device in /dev/mapper. The developers seem to be transitioning from the /dev/mapper id's to /dev/dm-* id's. The change is for the better but it keeps us wondering meanwhile!

---

### Post by LorenG on 2010-09-15
.. and now in Gparted I can't see the partitions anymore.
I have the /dev/mapper/nvidia_fagijdii listed as completely unallocated..
Although the old partitions seem to be still accessible from the live CD

..also I went to check the error and the long identifier is for the partition where Lucid is installed

---

### Post by ronparent on 2010-09-15
To see the partitions with gparted in 10.04 you have to install kpartx. In a teminal write:

> sudo apt-get install kpartx

Afterward gparted will find the raid partitions.:D

---

### Post by LorenG on 2010-09-16
Hey ronparent thanks, seems like I will have to give up on this one.
I had kpartx installed, in fact I could see the raid but it appeared as 400GB of unallocated space.Go figure..

In order to be able to see the partitions I had to use Mandriva again, then I deleted the Lucid partitions and reinstalled Mandriva. Now I have a bootloader that at least works with Win XP but still cannot load linux (Mandriva in this case).

Here's a pic of the screen message
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169624&d=1284627058[/IMG]

---

