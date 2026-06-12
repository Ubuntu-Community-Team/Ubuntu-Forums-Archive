---
title: "Why is 8.04 and 9.10 mounting USB hard drives read only?"
date: 2010-01-20
forum: General Help
---

### Post by wkulecz on 2010-01-20
Why are my Ubuntu 8.04 and 9.10 boxes mounting USB hard drives read only?  USB sticks still mount read/write.  Make them kind of hard to use :(

Actually "properties->volumes" shows rw in the mount options, but the permissions in /media/driveLabel are 755 root.root while USB sticks are 700 myuser.root

Seem to remember this was not the case before Thanksgiving, last time I plugged one in.

--wally.

---

### Post by Morbius1 on 2010-01-20
Here's my guess:

For  any External USB Mass storage device, stick or hard drive:

If it's formated in EXT3/4.... it will automount to root:root 755

If it's formatted in FAT32 ... it will automount user:root 700

Has nothing to do with hard drive vs stick. Has everything to do with whether it's been formated with a linux filesystem or a windows filessytem.

---

### Post by wkulecz on 2010-01-20
> Has nothing to do with hard drive vs stick. Has everything to do with whether it's been formated with a linux filesystem or a windows filessytem

Why?  Seems like a stupid idea to me.  

I know an ext3 formated USB stick mounted so my default user login could do drag and drop file transfer.

So how do I change this?  I sill expect the by user number and group number access restrictions to work, but I keep my default login user number the same.

This seems to have changed after 100+ updates between now and last time I connected these drives :(

--wally.

---

### Post by Morbius1 on 2010-01-20
Well I guess you've got a couple of choices:

You can change the ownership to your user name:

**sudo chown morbius1 /media/whatever**

Then the next time you plug it in it will be set as morbius1:root 755

Or you can leave the ownership as it is and change permissions:

**sudo chmod 777 /media/whatever**

Then when you plug it in it will mount with roor:root but with read / write permissions to anyone. This will make it easier to move to another machine ( at least another linux machine ).

Both of these methods don't change the ownership or permissions of the content of the drive it only affect the access to the drive. If you also want to change the contents add the "-R" option. For example:

**sudo chmod -R 777 /media/whatever**

---

### Post by wkulecz on 2010-01-20
This doesn't work as the automatically created mount point is removed when the drive is unmounted.

I tried chgrp myuser and chmod g+w before posting this.  I only do chmod 777 as an absolute last resort and -R is asking for trouble unless you know the only files below are user data files.

I assume somewhere in the udev scripts that run on usb insertion this distinction is made and could be changed.

--wally.

---

### Post by Morbius1 on 2010-01-20
>          This doesn't work as the automatically created mount point is removed when the drive is unmounted.I just did this myself on a ext3 formatted usb device.

sudo chown morbius /media/AZUL

Unmounted the device, unplugged it, and reinserted it and the device was mounted morbius:root.

Are you sure it's ext3?

---

### Post by wkulecz on 2010-01-21
Yes Im sure its formatted ext3.  The permissions will stick if I create the mount point so its there before insertion, but I don't want to have these in the /media directory when the device is not plugged in.

Maybe I'm remembering wrong, but USB drives used to mount with the same owner/permissions as USB memory sticks when I last did this back in Oct/Nov.

--wally.

---

### Post by Morbius1 on 2010-01-21
> The permissions will stick if I create the mount point so its there before insertion, but I don't want to have these in the /media directory when the device is not plugged in.
In my example ( which I just reverified on a Seagate usb drive ):
> sudo chown morbius /media/AZUL Ubuntu created the /media/AZUL mount point upon insertion, I didn't.  AZUL is the label on that drive. If I chown, then unmount and disconnect the drive, the /media/AZUL mount point goes away. If I reinsert the drive the mount point is recreated and the ownership follows my previous chown command.

I'm really beginning to think there is something wrong with your hard drive or maybe the port that you're plugging it into.

---

### Post by chooseopen on 2010-02-04
Did you ever resolve this?  I have the SAME issue in 9.10.
In my case, the auto-mount action creates the folder: /media/38eba267-7769-4411-8dec-a90474900758/ (most likely because I dont have a drive label set).
Like you, the folder is deleted when the device is unplugged and re-created when it is plugged back in so I cant really set permissions on it.

---

### Post by wkulecz on 2010-02-09
> I'm really beginning to think there is something wrong with your hard drive or maybe the port that you're plugging it into.

You might think this but you'd be wrong.  If I do  sudo -i, as root I can write the drive fine. As my default user I can read what little it has access to.

No I've not resolved it.  Some updates came in Friday, haven't had time to try them yet, perhaps a fix is in these somewhere.

---

### Post by cloyd on 2010-02-09
I am having a similar problem in UNR 9.10.  I cannot mount my seagate external hard drive, nor any Sanddisk Cruzer drive. Plugging either one in seems to result in something like "mount  exited with error code 1: helper failed"  and then more. In 9.10, I can mount with gparted, Mount point is media/cdrom0. Cannot use the drive because I am denied perimssion, but I can see what is on it. I must unmount with gparted also. 

Usb drives (flash and external hard) work without problem on another machine running 9.04.  I'd really like to figure this out.  I've started threads, without much response. 

Does the mount point of media/cdrom0 have anything to do with it?

---

### Post by wkulecz on 2010-04-02
I've had issues with recent USB sticks and external hard drives having some kind of "cdrom partition" with lame Windows software on them.  These have wreaked havoc with using the devices on my ubuntu 6.06 & 8.04 systems.  This is ridiculous!

At least Western Digital had a firmware change I could download to remove the cdrom partiton so the MyBook 2TB now workd for me.  See if Seagate and SanDisk have similar.  It was combursome and had to be don on a Windows box :(

Googling suggests that removing the cdrom partition from USB sticks is difficult to impossible.

---

### Post by mkvnmtr on 2010-04-02
Over the years I have had lots of problems with nounting. Works a while and then it does not. Make a mount point and then things change. Lately I have been installing a program called pmount. I have no idea just what it does. It says it lets a user mount devices. Since using it I rarely have any problem. Found it in synaptic.

---

