---
title: "grub, menu.lst, auto detect other os"
date: 2009-08-28
forum: General Help
---

### Post by Andreas1 on 2009-08-28
it is easy to explain what i want:
detect all operating systems on my computer and updates menu.lst accordingly, like when installing ubuntu.

what i tried so far:
```
update-grub
```
it creates a new menu.lst (only if i delete the old one first, but ok...) containing only the kernels from the system on which i am running update-grub, no other os

---

### Post by Andreas1 on 2009-08-29
bump

---

### Post by Herman on 2009-08-29
GRUB2 can do that, but with GRUB legacy most of us still edit the /boot/grub/menu.lst file by hand when we want to add more operating systems.

The best kind of command to use for booting other operating systems is the chainloader command, and the other operating system needs to have its boot loader installed to it's partition (boot sector), or to a MBR for that to work.

Karmic Koala will have GRUB2 by default, and you can install GRUB2 in Jaunty Jackalope or Intrepid Ibex, but probably it's not recommended for normal users yet. Besides, it has a habit of listing every kernel in every operating system, making a huge long list a person needs to scroll through to find the right boot entry, so it's still best to edit by hand. Later there will probably be scripts and programs made for GRUB2 so users will be able to manage it from GUI. One such program is 'Start Up Manager', andit's already available but it doesn't yet do what you want to do at this time. Maybe some day in the future it will be updated with the features you're asking for.

Do you need help with manual editing? 
If you do then if you can provide more information about your specific setup someone should be able to help you.

Regards, Herman :)

---

### Post by renebs on 2009-10-02
Hi,

I would like some help with the same issue of Andreas1. I have vista on /dev/sda1, ubuntu 8.04 on sda3 and ubuntu 8.10 on sda5. I use 8.10 from day to day (but given some hardware issues, sometimes I use the 8.04 as well, as a backup). I've installed 8.04 after 8.10, and therefore the grub that is running is from the /boot folder found on /dev/sda3. I would like to have the grub found on my sda5 being the master one and add the boot of /dev/sda3 in chainloader as you suggested. 

So, finally, the question: how to edit my menu.lst and which?

---

### Post by renebs on 2009-10-02
So, I have added the boot sda5 to mbr. Following Herman tutorial, basically have done this (from within the ubuntu 8.10 booted from sda5)
$grub> find /boot/grub/stage1
$grub> root (hd0,4)
$grub> setup (hd0,4)

Now, I have added to my menu.lst:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		OS-on-sda3 (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

Note that this was an exact copy of the chainloader config for the OS on sda1. It didn't work, got an error message. 

Any idea will be helpful. Thanks

---

### Post by renebs on 2009-10-02
Ok.
I decided to copy my old menu.lst (created during installation of ubuntu 8.04) with the necessary modifications and it worked. 

Basically it had originally something like:
> title           Ubuntu 8.04, kernel 2.6.24-16.30-generic
uuid            5a4ce692-a96d-4b72-9fa4-cfed1d2da21f
kernel          /boot/vmlinuz-2.6.24-16.30-generic root=UUID=5a4ce692-a96d-4b72-9fa4-cfed1d2da21f ro quiet splash 
initrd          /boot/initrd.img-2.6.24-16.30-generic
quiet


And I changed to something like: 
> title           2nd-Ubuntu 8.04, kernel 2.6.24-16.30-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16.30-generic root=UUID=5a4ce692-a96d-4b72-9fa4-cfed1d2da21f ro  single
initrd          /boot/initrd.img-2.6.24-16.30-generic
savedefault
boot


and added before the sda1 boot option.

---

### Post by renebs on 2009-10-02
Ok.
I decided to copy my old menu.lst (created during installation of ubuntu 8.04) with the necessary modifications and it worked. 

Basically it had originally something like:
> title           Ubuntu 8.04, kernel 2.6.24-16.30-generic
uuid            5a4ce692-a96d-4b72-9fa4-cfed1d2da21f
kernel          /boot/vmlinuz-2.6.24-16.30-generic root=UUID=5a4ce692-a96d-4b72-9fa4-cfed1d2da21f ro quiet splash 
initrd          /boot/initrd.img-2.6.24-16.30-generic
quiet


And I changed to something like: 
> title           2nd-Ubuntu 8.04, kernel 2.6.24-16.30-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16.30-generic root=UUID=5a4ce692-a96d-4b72-9fa4-cfed1d2da21f ro  single
initrd          /boot/initrd.img-2.6.24-16.30-generic
savedefault
boot


and added before the sda1 boot option.

---

### Post by oldfred on 2009-10-02
It would have been better to have started your own thread to avoid confusion with the OP.

While you seem to have answered most of your own questions. To chainboot you have to install grub to the partition. You installed to (hd0,4) but then you tried to boot from 		(hd0,2)

One of my chainboot entries:
title       Ubuntu 9.04 Jaunty 64 bit @ sdc5
root        (hd2,4)
chainloader +1

From running boot_info_script032.sh 
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc5 and 
                       looks at sector 216198297 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Herman on 2009-10-02
Hello renebs,
Intrepid Ibex's GRUB is far superior to Hardy Heron's GRUB as a boot manager because Intrepid Ibex's GRUB uses file system UUID numbers instead of device names for specifying which partition contains the files you want to boot.
That means we can add or remove hard disks and USB drives and boot without needing the menu.lst to be edited every time. 

The chainloader command is preferred to a direct kernel boot in boot stanzas for dual or multi booting with more than one Linux because that way we're using the other Linux's boot loader to do the actual booting with, using it's own menu.lst file. The other operating system keeps it's own menu.lst file up to date automagically each time it receives a new kernel so we won't need to do that manually, which can get to be a chore. The chainloader command has the added advatage of being able to boot any other boot loader in case you have LiLo or GRUB2 in the other operating system. In your case that's not important but I'll use the chainloader command rather than a symlink boot this time anyway because it's generally better and it might help someone else who might be reading this post.

[LIST=1]
[*]we'll use GParted to set file system labels in your Hardy and Intrepid partitions to make things easier now and in the future, (only if you haven't already done so).
[*]we'll install your 8.04's GRUB to your 8.04 partition boot sector so you can chainload it and use it as the boot loader for 8.04.
[*]we will edit your 8.10's /boot/grub/menu.lst file to include a chainloader boot stanza for 8.04
[*]we'll install your 8.10's GRUB to MBR
[/LIST]
It would be easiest to do this from your Ubuntu Intrepid Ibex 'Desktop' Live/Install CD.

---

### Post by Herman on 2009-10-02
1. File System Labels
(i) Boot your Ubuntu Intrepid Ibex live CD and open a terminal and,
(ii) Open GParted by clicking 'System'-->'Administration'-->'Partition Editor'
(iii) Right-click on your Ubuntu Hardy Heron partition and in the right-click menu click 'Label'
(iv) Give your Hardy Heron file system a user friendly name, 'HARDY' will do if you're not sure.
(v) Right-click on your Ubuntu Intrepid Ibex partition and in the right-click menu click 'Label'
(vi) Label your Intrepid Ibex file system with a friendly name, 'INTREPID' is an obvious suggestion.
(vii) Click 'Apply', and then 'Apply' again to confirm.
(iix) If there isn't anything else you want to use GParted for right now, you can close GParted. One suggestion would be to run a file system check in each of your Ubuntu file systems while you have GParted open though, if you have a few minutes of spare time. It's always a good idea to run a file system check at any convenient opportunity. After that you can close GParted.
(ix) reboot

NOTES: Verbose explanations with illustrations can be found at 
[Click-Icon Mounting]("http://members.iinet.net.au/%7Eherman546/p10.html#Click-Icon_Mounting") - shows the modern (easy) labeling method in the last two illustrations
[Make a label for your ext3 file system]("http://members.iinet.net.au/%7Eherman546/p10.html#ext3_usbdisk_labelling") - traditional method

---

### Post by Herman on 2009-10-02
2. Install 8.04 Hardy Heron's GRUB to Hardy Heron partition boot sector.
With your Ubuntu Intrepid Ibex Live/Install CD rebooted and running in your computer once again,
(i) Open GRUB as a program with superuser powers,
```
sudo grub
```
(ii) run a quick test to determine which partition(s) contain(s) GRUB files, for safety's sake,
```
find /boot/grub/stage2
```
(iii) If the results of the above test indicate that you have a /boot/grub/stage2 in both (hd0,2) and (hd0,4) then choose (hd0,2) as the partition to focus GRUB's attention to,
```
root (hd0,2)
```
(iv) Install code from the /boot/grub/stage1 to the partition boot sector in (hd0,2) to make that boot sector point to the /boot/grub/stage2 file in (hd0,2), which is your Hardy Heron partition.
```
setup (hd0,2)
```
(v) Exit from GRUB for the time being,
```
quit
```

NOTES: Some new websites are skipping the important test for checking which partitions contain GRUB. It's best to always make sure we're installing GRUB's IPL code to a Linux partition. If we neglect to advise people about the safe way someone will make a mistake and install it to their Windows partition and cause themselves some inconvenience. In that case we might as well just have used the grub-install command instead. The grub-install command has the advantage of refreshing the GRUB files in /boot at the same time as installing GRUB's IPL to a MBR or to a boot sector.

---

### Post by Herman on 2009-10-02
3. Edit Intrepid Ibex's /boot/grub/menu.lst with a boot stanza for chain loading Hardy Heron's GRUB by the partition boot sector.

(i) Mount your Intrepid Ibex partition's file system, 'Places'-->'Removable Media'-->'INTREPID'

(ii) Open Nautilus with superuser powers
```
gksudo nautilus
```(iii) Navigate to your /media/INTREPID/boot/grub/ directory and open your Intrepid Ibex /boot/grub/menu.lst file.

(iv) Type, (or copy and paste) a boot stanza in for chain loading your boot loader in your Hardy Heron partition by the boot sector.
Your Hardy Heron boot entry must not be placed within the Debian automagic kernels list which is marked by signs in upper case letters at the top and bottom.
For example,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title        Ubuntu Hardy Heron Chainloader boot on /dev/sda3, (hd0,2)
uuid=xxxxxxxxxxxxxxxxxxxxxxxxx
chainloader +1
```Where: xxxxxxxxxxxxxxxxxxxxxxxxx is the uuid number for your Ubuntu Hardy Heron file system, to find that open a terminal in another workspace and run 'sudo blkid'. Copy and paste the correct uuid number for Hardy Heron here.
```
sudo blkid
```(v) save the changes, close the file, exit nautilus and close any other open programs and files

---

### Post by Herman on 2009-10-02
4. Install 8.10 Intrepid Ibex's GRUB to MBR in your first hard disk

(i) Open GRUB as a program with superuser powers again,
```
sudo grub
```(ii) run a quick test to determine which partition(s) contain(s) GRUB files, for safety's sake,
```
find /boot/grub/stage2
```(iii) If the results of the above test indicate that you have a /boot/grub/stage2 in both (hd0,2) and (hd0,4) then choose (hd0,4) as the partition to focus GRUB's attention to, because that should be your Intrepid partition,
```
root (hd0,4)
```(iv) Install code from Intrepid's /boot/grub/stage1 to MBR in your first hard disk and stage1_5 of GRUB to the next 21 sectors of the first track of the hard disk, to point to the /boot/grub/stage2 file in (hd0,4), which is your Intrepid Ibex partition.
```
setup (hd0)
```
(v) Exit from GRUB,
```
quit
```

Reboot  and make sure it works!

---

