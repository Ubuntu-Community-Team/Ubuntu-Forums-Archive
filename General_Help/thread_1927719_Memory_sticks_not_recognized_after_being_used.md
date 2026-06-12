---
title: "Memory sticks not recognized after being used"
date: 2012-02-18
forum: General Help
---

### Post by BADGER.BRAD on 2012-02-18
Hello all,

I have a problem using Xubuntu but not Ubuntu by right clicking over the memory stick in Ubuntu I get the option to format the drive which works no problem, in Xubuntu I do not get this option using Gparted to format the drive fat32 and now the drive is not recognized and does not show up on the desk top although Gparted shows the drive and doing sudo fdisk -l also shows it. I seem to have wrecked multiple memory sticks using Ubuntu in it's various forms, is there anyway to get them back ? In Xubuntu deleting the files from the memory stick stops them being seen but does not seem to free up the disk space being used by them. If I then put my memory stick in my stereo all the files including the deleted ones can be played. Has anyone any idea what is going on ? I'm too scared to try using my last memory stick :(

Many thanks
 
Brad

---

### Post by Paddy Landau on 2012-02-19
Brad, please do not type **everything in bold**. It makes it hard to read.

First: I am a bit confused about where you can and cannot see the memory stick.

After you format the stick from GParted, it may no longer be mounted, hence why it does not show up. Try using Disk Utility instead, where you can mount the device after formatting it.

Second: When you delete a file in Nautilus, as with Windows it does not actually delete it but moves it to the Trash (Rubbish Bin or Recycle Bin). That is why your stereo still recognises the file. To delete the file permanently, either press Shift while deleting the file or empty the Trash after you have deleted it.

---

### Post by BADGER.BRAD on 2012-02-19
Thanks for the reply Paddy, Sorry about the message being in bold I had cut and pasted it from elsewhere and had not realized. The memory stick fails to show on the desktop after format but still shows in Gparted and  by doing sudo f-disk. The problem always begins with the fact that Linux will not delete the files fully so will not release the the full size of the drive again. It seems to be O.k to begin with but then I find I have to delete the files and then wipe the drive with Bleachbit this seems to work again for a while until a point where the files are not deleted but will not show on looking at the contents of the memory stick ( although they are still there  as show by free space size) then as Bleachbit will only wipe free space I cannot free up the full drive again. Using Gparted after a while seems to finish the memory stick off to the point it then will not show on the desktop. This has happened to a number of memory sticks I have used. I am formatting them as fat32.

 Hope this makes some sort of sense , As I wish to set up a spare pc without a harddrive to boot from Memorystick I don't wish to go to the expense of using a relatively large/expensive memory stick if it is going to be destroyed.

Many thanks Brad

---

### Post by Paddy Landau on 2012-02-20
I think I have a better understanding of your problem, Brad.

> **BADGER.BRAD said:**
> ... Linux will not delete the files fully...

As I already said, to delete a file  permanently, either Shift-Delete or empty the Trash (Bleachbit would be  emptying the Trash). You do not have to keep reformatting.

That should solve your problem in future.

> **BADGER.BRAD said:**
> Using Gparted after a while seems to  finish the memory stick off to the point it then will not show on the  desktop.

Again, as I said, it might simply have been unmounted for the reformatting. If you have reformatted your stick and now it is not mounted, just mount it. You can do that in any one of the following ways:

[LIST]
[*]Reboot.
[*]Log out and in again.
[*]Open Disk Utility and mount from there.
[*]Unplug the USB stick, then plug it in again.
[/LIST]
There are other ways, but those are the easiest that I know of. There is probably a way to mount it from Thunar (I don't use Xubuntu, so I don't know how to use Thunar). Choose the one you prefer.

---

