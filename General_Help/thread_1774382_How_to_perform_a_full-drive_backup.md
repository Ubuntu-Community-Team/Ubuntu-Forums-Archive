---
title: "How to perform a full-drive backup"
date: 2011-06-03
forum: General Help
---

### Post by mac9416 on 2011-06-03
Hi, y'all,

I am a backup noob. My idea of backing something up is finding a big enough flash drive and copying the necessary files over.

So I really need to learn now. I'm wiping a Vista laptop for a friend to install Windows 7. But first, I want to do a whole-drive backup in case something goes wrong. It's a 100GB drive with 50GB of data.

Is it possible that I could do this via my home network or via a direct ethernet connection? I have a desktop with a 1TB drive I could back up to. Like I say, I'm a noob so I'm open to anything.

One more thing: I'd like this backup to be in a form that I can retrieve individual files from it if necessary. If everything goes right, I'll probably want to pull My Documents out of the backup and drop it into Windows 7.

Oh, and why am I asking on UbuntuForums instead of a Windows forum? Because I'm betting I'll end up booting a live CD on the laptop to do the backup. But I'm just guessing. At any rate, I'm sure I'll use Ubuntu tools, because that's what I know.

Thanks for any suggestions!

---

### Post by ratcheer on 2011-06-03
Download CloneZilla and put it on the bootable media of your choice. It will make a full image of your current system that can be used to completely restore it, if necessary.

You can not, however, use it to restore selected files or folders. It creates a disk image, not a file-by-file backup.

Tim

---

### Post by mac9416 on 2011-06-03
Hey, ratcheer, thanks for the suggestion. What can I use as a backup destination? Can I send the image over an ethernet connection to my 1TB machine?

---

### Post by linkageless on 2011-06-03
I've not used clonezilla, but it sounds promising.

In similar situations, my approach has been to use dd, perhaps piped through other tools.

So an example command line without compression, assuming we are backing up the entire (unmounted) filesystem on /dev/sda1 into a file on our usb disk on /media/disk/ would be:
dd if=/dev/sda1 of=/media/disk/vista-image-sda1-20110603.dd

This should result in a file the exact size of the original partition, which you could then gzip or bzip2 if you had the time & space.

Uncompressed, this image file can be mounted through a loop device:
mount -o ro,loop /media/disk/vista-image-sda1-20110603.dd /mnt

(I've used the read only flag here assuming you want to keep the image pristine. You might need to use a -t option to specify filesystem depending on your kernel.)

If I'm keen to save space, I'd pipe it through bzip2 as I'm doing the dd. To save more space on that bzip2'ed archive, I'll fill the 'empty' space beforehand on the filesystem with a file full of zeros which is much more compressible for bzip2 than the detritus of old files. This can be done using dd from /dev/zero, and actually deleted before the archive is taken, but I would be reluctant to do this to an ntfs filesystem if it needed to be exactly 'as was'.

---

### Post by psusi on 2011-06-03
dd is NOT a backup utility!

Reasons not to use dd:

1)  It wastes time and space copying unused sectors
2)  Can not restore to a smaller disk, even if the original was nowhere close to being full
3)  It preserves any fs corruption or fragmentation
4)  It is very easy to get the arguments wrong and trash your system

dd is a swiss army knife for when you are stuck deep in the woods and your arm is pinned under a rock and you have to saw it off, and don't have anything else handy.  For most tasks, there are other tools that are much better suited.

---

### Post by ratcheer on 2011-06-03
> **mac9416 said:**
> Hey, ratcheer, thanks for the suggestion. What can I use as a backup destination? Can I send the image over an ethernet connection to my 1TB machine?

I'm not sure. I always use it with a locally connected external USB drive. You can check out the specific features, here:

[http://clonezilla.org/](http://clonezilla.org/)

Tim

---

### Post by linkageless on 2011-06-03
I agree with the sentiment about dd being a swiss army knife, it is simple yet powerful and hence dangerous. However, in my experience, preserving a windows filesystem exactly as-is is the safest route. YMMV

If you were only interested in the contents without needing to resurrect the os at a later date, then perhaps other higher level tools would be most appropriate.

---

### Post by HotForLinux on 2011-06-03
I can't give you the details right now but an idea would be to use the **rsync** program in linux (there are versions for windos too), which is like a versatile copy command,  to transfer the files over the network: as an image, a compressed file, the interesting folders,.... any way you choose. You will need to establish either a telnet or a ssh connection between the laptop and the desktop. An ssh client running on one of them and a ssh server on the other (same with telnet, which is more or less the same but ssh encrypts the transmission).  You can download an excellent free ssh client for windows called **putty**.

In ubuntu, even with the live cd, it is easy to install and run the ssh server. 

To connect to the ssh server you will need to know the local **ip address** of the computer running the server, a user and its password (so you need to establish a known password for the default user, if you booted that pc with the Live-CD).

If you boot the laptop with the Live CD, you will have to mount the partitions  that you want to work with. And you will need to take care of the permissions.

Maybe it would be a good idea to use a case to connect the desktop's HD to the laptop's USB, as an external drive and avoid using the complicated instructions to use the network.

---

### Post by mattgyver83 on 2011-06-03
Alongside Clonezilla exists partimage which is also handy though not as packed with features.  No matter the utility that you use I highly suggest if your looking for a way to really explore all your options (dd, clonezilla, partimage) download the PartedMagic live distro.  Its great, real small, has all the system tools you could ever need for this sort of thing or just repair/diagnostics.

I should add that it includes all the packages so far mentioned in this thread and has an easy network setup to get you up and running and still use the computer if need be while your down for maintenance.

---

### Post by mattgyver83 on 2011-06-03
> **mac9416 said:**
> Hey, ratcheer, thanks for the suggestion. What can I use as a backup destination? Can I send the image over an ethernet connection to my 1TB machine?

There are ways to do this, easiest if you have an SSH server setup.  Another option is share out a folder (either on a windows box or via samba), mount the share and specify the directory as your storage repository in clonezilla.  Off memory I cant give you better details than that, hope it helps though.

---

