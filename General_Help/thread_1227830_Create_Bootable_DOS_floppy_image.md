---
title: "Create Bootable DOS floppy image"
date: 2009-07-31
forum: General Help
---

### Post by asai on 2009-07-31
Hi,
I am trying to make bootable floppy image files for use in Virtualbox. I have the files from the the MS-DOS floppies on my computer.

I have tried this:
```
dd if=/dev/zero of=floppy.img bs=512 count=2880
mkdosfs floppy.img
sudo mkdir /media/image
sudo mount -o loop floppy.img /media/image
sudo nautilus /media/image

```
Copied the files to the mount, then
```
sudo umount -l /media/image
```
Then I tried to start my DOS Virtualmachine in Virtualbox.
But it stops with error: "This is not a bootable disk"
What's wrong with the image file?

Ref this page: [http://ubuntuforums.org/showthread.php?t=140762]("http://ubuntuforums.org/showthread.php?t=140762")

---

### Post by spcwingo on 2009-07-31
If all you need is a basic DOS boot floppy to update a BIOS, you can download a FreeDOS based boot disk [[COLOR="Red"]here[/COLOR]]("http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz"). Extract it,  then write it to disk with this command:

```
dd if=/path/to/FDOEM.144 of=/dev/fd0
```

I have used FreeDOS boot disks to update the BIOS on many of my machines.

Now, if this isn't the case at all, please post back with specifics of what it is you're trying to accomplish and I'll try to give you a hand to the best of my abilities.

EDIT:  I didn't see the part about trying to run DOS under VBox.  Still, if all you need is a DOS environment to run old programs/games try FreeDOS.  You can read more about it [[COLOR="Red"]here[/COLOR]]("http://www.freedos.org/")

---

### Post by asai on 2009-07-31
Thanks for your reply.

I have MS-DOS 4.01 on 4 .dsk file format images. These images I have succesfully extracted, and are now trying to make .img files of them. This I have accomplished with the command in my previous post. However, I want to boot from this image with Virtualbox. This doesn't work.

---

### Post by spcwingo on 2009-07-31
Have you tried to just change the extension?  If that doesn't work just put the floppies back in your machine and use dd to extract the images.  Example:

```
dd if=/dev/fd0 of=/home/asai/disk1.img
```

You could always just use the floppies under VBox...just mount your host drive.  :)

---

### Post by asai on 2009-07-31
If I had a floppy drive I could, but I don't... ;)
That's the reason why I would like to use image files to boot my virtual machine. The image contains all the system files needed to boot, but it doesn't have the boot record. Is this correct?
So, the solution is to get them into the image like bootable iso CD images...

---

### Post by angry_johnnie on 2009-07-31
Why not just download a floppy image?
or a cd iso image?

You can get DOS 7.10 from [here]("http://ms-dos7.hit.bg/index.htm").  It has a lot of nifty features.

---

### Post by lykwydchykyn on 2009-07-31
Well it's been a few years from the DOS days, but if memory serves copying the files wasn't enough to make a bootable floppy.  You had to run the "sys" command which I presume installed some sort of boot sector to the disk.

I don't know what a .dsk file is, but if the filesize is 1.4 MB then it's likely they are just straight images.  There's no real standard file extension for floppy images, I've seen people use .img, .flp, .144, and other things.  Where did these files come from?

---

### Post by Chronon on 2009-07-31
Or download a fresh .iso from the freedos site: [http://www.freedos.org/freedos/files/](http://www.freedos.org/freedos/files/)

---

### Post by matey3 on 2009-07-31
> **lykwydchykyn said:**
> Well it's been a few years from the DOS days, but if memory serves copying the files wasn't enough to make a bootable floppy.  You had to run the "sys" command which I presume installed some sort of boot sector to the disk.

I don't know what a .dsk file is, but if the filesize is 1.4 MB then it's likely they are just straight images.  There's no real standard file extension for floppy images, I've seen people use .img, .flp, .144, and other things.  Where did these files come from?

yeah lol, good old days...
I remember doing sys a: or use quick format command like format a: /q /s to put the system on the disk.

I remember downloading a linux boot disk once which came with this program (may be called flash?) I dont remember really but that .exe file would put the system on the disk and make the computer boot.
anyway you are right that DOS machines require a special boot disk where the system file go on specific location on the disk, whereas the linux you can just copy the files you need to boot with.
I also usd to visit bootdisk.com a lot I dont know if it still exits?

---

### Post by lykwydchykyn on 2009-07-31
> **matey3 said:**
> anyway you are right that DOS machines require a special boot disk where the system file go on specific location on the disk, whereas the linux you can just copy the files you need to boot with.
?

Well, not really; with any OS you have to have a proper boot sector in place.  GRUB or LILO take care of that for you in Linux, or for a floppy you'd use something like syslinux.

---

### Post by asai on 2009-07-31
> **angry_johnnie said:**
> Why not just download a floppy image?
or a cd iso image?

You can get DOS 7.10 from [here]("http://ms-dos7.hit.bg/index.htm").  It has a lot of nifty features.

I have a lot of virtual machines in my Virtualbox, which have been installed using cd iso images.
But now I would like to install MS-DOS 4.01 which I have all the files extracted from .DSK files.
So, is there then a way to create a boot-able cd image with these files?
Instead of floppy images?

---

### Post by asai on 2009-07-31
> **matey3 said:**
> 
I also usd to visit bootdisk.com a lot I dont know if it still exits?
Well, I have tried going to that site for the hole day, but this message is what I get: ```
Bandwidth Limit Exceeded
The server is temporarily unable to service your request due to the site owner reaching his/her bandwidth limit. Please try again later.
Apache/1.3.37 Server at bootdisk.com Port 80
```
[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by lykwydchykyn on 2009-07-31
> **asai said:**
> I have a lot of virtual machines in my Virtualbox, which have been installed using cd iso images.
But now I would like to install MS-DOS 4.01 which I have all the files extracted from .DSK files.
So, is there then a way to create a boot-able cd image with these files?
Instead of floppy images?

I know it can be done in K3b, I would assume it can be done in whatever GNOME ships as a CD burner.  But the quick and easy way is at the command line:
```

mkisofs -b msdos.dsk -o msdos.iso msdos.dsk

```

That's assuming your .dsk file is called 'msdos'.  It will give you a bootable iso file called msdos.iso.

---

### Post by asai on 2009-08-01
The command:
```
mkisofs -b /home/terje/dos401/DISK1.DSK -o msdos.iso /home/terje/dos401/DISK1.DSK
```
The result:
```
I: -input-charset not specified, using utf-8 (detected in locale settings)
call to search_tree_file with an absolute path, stripping
initial path separator. Hope this was intended...
genisoimage: Uh oh, I cant find the boot image '/home/terje/dos401/DISK1.DSK' !
```

---

### Post by lykwydchykyn on 2009-08-01
> **asai said:**
> The command:
```
mkisofs -b /home/terje/dos401/DISK1.DSK -o msdos.iso /home/terje/dos401/DISK1.DSK
```
The result:
```
I: -input-charset not specified, using utf-8 (detected in locale settings)
call to search_tree_file with an absolute path, stripping
initial path separator. Hope this was intended...
genisoimage: Uh oh, I cant find the boot image '/home/terje/dos401/DISK1.DSK' !
```

Try the command in the same directory with the DISK1.DSK file and drop the paths, e.g.:
```

cd /home/terje/dos401
mkisofs -b DISK1.DSK -o msdos.iso DISK1.DSK

```

---

### Post by asai on 2009-08-02
Here is the result of the command without path:
```
genisoimage: No such file or directory. Invalid node - 'msdos.iso'.

```
When I used the full path, the msdos.iso file was created, but it wasn't bootable. Now it didn't get created.

---

### Post by lykwydchykyn on 2009-08-02
Well, I don't know what that means exactly.  The command works fine for me here with a bootable floppy image.

Maybe try running:
```

file DISK1.DSK

```
To see if you can determine what the .DSK file actually is.  Maybe it's not a normal disk image.

Are you sure the directory you're working in is writeable?

If nothing else, install qemu and see if the .DSK file will boot using:
```

qemu -fda DISK1.DSK -boot a

```

Really don't know what else to suggest.

---

### Post by asai on 2009-08-02
OK, the image may be corrupted or something.
Here's what I get:
Running file DISK1.DSK
```
DISK1.DSK: data
```
When I launch qemu like you described, it stops with:
```
Booting from Floppy...
Boot failed: not a bootable disk
FATAL: No bootable device
```
I have managed to extract the contents of the file, and now this is the system files from dos. Is there then anyway to make the image bootable?

---

### Post by asai on 2009-08-11
Here is my solution: [http://ubuntuforums.org/showthread.php?p=7769811#post7769811]("http://ubuntuforums.org/showthread.php?p=7769811#post7769811")

---

### Post by morrie on 2011-04-24
Why not one thing at a time? why do we always have to wade through someone's spoon-fed tutorial on how to do something really really rare and esoteric that noone ever does.  

Who uses floppies??  Can we get someone smart to give us a solution that does not require antiquated technology?

Maybe you can fax it to me?

I am so daunted by the fact that this post is four hundred pages long.  Should this be a relatively easy thing to do?  WHY IS IT SO HARD???????????????

Ubuntu 10.04.  4th hour trying to make a (raSS--a-FRass-in) dos-bootable SEATOOLS DISK.

Yes, I blame _Seagate_ (_used to be a good company_) for being such lazy bastards.  Why can't they just post a bootable USB image of their (almost useless) tool?  They want us to actually install a floppy drive in our computers. I,FOR ONE, REFUSE!!!!

---

### Post by mkulon on 2011-05-30
To create new UNFORMATTED floppy disk image on linux / ubuntu if your system does not have a floppy drive:

dd bs=512 count=2880 if=/dev/zero of=floppy.img

You will then need to mount it in (e.g in virtual box) and format it.

For those that need a Windows FAT formatted blank floppy, I am also attaching a formatted floppy image.

---

### Post by AwesomeMachine on 2011-10-03
[B]Most MS DOS install disks are filled with compressed files, except for a few such as command.com, sys, io.sys extract and msdos.sys. If you want to install DOS into a virtual machine, you need the install disks. If you have the install disks, you have the install disks. If the emulator boots DOS, you just dd the floppies to image files, and boot the first disk. 

If you copied the files off the install disks, into directories, then you need FDOEM.144.gz from the freedos site. Make a backup of FDOEM. Gunzip it, mount it somewhere, and delete everything but command.com, io.sys, sys and msdos.sys. 

Copy the files you saved from the first DOS install disk, to the FDOEM144 mounted floppy image. OK, your done. Umount it, and that's the first--read: bootable--install disk. There's a couple of different ways to go from here, but you can just put the files from the remainder of install disks into a pile somewhere where the emulator can find them. 

When the installer asks for the next disk, just point it to wherever you put the rest of the files. But MS DOS is pretty silly. Freedos gives you a lot more features, like graphical user interface and web browsing. OH, and Internet connectivity. Plus, it's got all the coreutils tools for DOS. AND, it comes as a bootable iso9660 file, so you just boot and install off that. 


[/B]

---

