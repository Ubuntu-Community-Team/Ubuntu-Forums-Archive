---
title: "Encrypted data partition and fresh install"
date: 2011-06-29
forum: General Help
---

### Post by Djalmahal on 2011-06-29
Hi,

I'm having a data and an OS partition, currently running 10.10. I would want to do a fresh install of 11.04 on the OS partition and keep the data partition. The problem is I can't find the key I was given at my last install for the encrypted partition and I assume with a fresh install the data partition would become unreadable.

So what can I do, is there a way to retrieve the key through a terminal command or so?

Thanks for your help
Andreas

---

### Post by Herman on 2011-06-29
I'm not sure about exactly what kind of encryption you're using but I use [dm-crypt]("http://www.saout.de/misc/dm-crypt/") with [LUKS]("http://code.google.com/p/cryptsetup/") and I haven't noticed any problems accessing the data from more than one Ubuntu installations. Maybe yours is set up different or special and there's something more I haven't learned yet. 

In my case at least, I only need to make sure I remember the password.

If you're not sure and you want to be safe, install Ubuntu in an 8GB or larger USB flash memory stick and install cryptsetup and run 'sudo modprobe dm-crypt' and after that test to see if you can mount your encrypted file system and read and write to it. 
If it's in LVM you might want to install lvm2 as well, I'm not sure if you'll need it but it won't hurt.

It's a good idea to have an auxilliary operating system if not in a USB stick then possibly in some other drive, it can be very convenient if you ever run into problems with your main installation.

Once you're confident you'll be able to access your encrypted files okay (I hope) from the flash memory installation it would be a good idea to use the dd command for making a backup of at least the first two sectors of your encrypted data partition since those are unique and may be needed to help regain access to your data in some circumstances.
Something like,
```
sudo dd if=/dev/sda2 of=2011-06-30_luksheader.img count=2
```where: /dev/sda2 is your encrypted data partition, as shown by the results from 'sudo fdisk -lu' and 'sudo blkid'.
That command will save the first two sectors of your encrypted partition and with any luck you'll never need to restore those two sectors anyway, but the backup doesn't take up much room and it's nice to know you have it. Keep it in your USB auxilliary Ubuntu maybe.

By the way, it's quite alright to make your auxialliary USB Ubuntu installation an encrypted one too, I have a couple of USBs like that already and I'm quite happy with them. Encryption is probably more important for a USB than for a internal drive.

It's probably a good idea to make another encrypted partition in some other hard drive too, for making a backup of files in your first encrypted partition in, just in case anything bad happens suddenly to the hard drive like the sudden fusion of some small electronic part in the drive's circuit board or something like that. Things like that are fortunately relatively rare, but they can and do happen occasionally.

---

### Post by Djalmahal on 2011-06-29
I know recovered the encryption key through a command, how do I use it on a fresh install, i.e. tell the new install to use this to unlock the /home partition?

---

### Post by Djalmahal on 2011-06-29
Ok, making a USB now and I'll try it out.

Once I go ahead with the install will it ask me for the passphrase or do I have to do that through a command?
The encryption is the standard Ubuntu encryption as set up in a previous install

---

### Post by Herman on 2011-06-29
If you can explain specifically what kind of arrangement you have set up there. somebody might be able to give you specific help.
Is there a link to a web page with a how-to or tutorial you followed for information about this 'encryption key'?
Maybe you will be the one teaching me a new trick. I know there is a lot I don't know yet. :)

... oh,
> Once I go ahead with the install will it ask me for the passphrase or do I have to do that through a command?
The encryption is the standard Ubuntu encryption as set up in a previous installYou will need at least these two comamnds, (or at least those are the two commands that seem important for me I do it).
You only need to run these once in a new install and then they will remain good for the life of the OS,```
sudo apt-get install lvm2 cryptsetup              
``````
sudo modprobe dm-crypt
```After running those two commands, look in your 'Places' menu for the encrypted partition.
When you click on it to try to mount it you should be prompted for your encryption password, but it will say something like 'failed to mount encrypted file system', and make you think it didn't work. Nevermind, go back to your 'Places' menu and look and hopefully you should see a new icon there for your encrypted file system, click on that one and now you should see your files.
Recently I have also needed to chmod the mount point for write permission, I'm not sure if there have been recent software changes or because I'm doing special experiments and tricks.

---

### Post by smurphy_it on 2011-06-29
I've hit issues like this when attempting to resize an encrypted partition.  You basically have to do a ```
sudo apt-get install lvm2
```, followed by loading the module ```
sudo modprobe dm-mod
```and then decrypt your EFS by supplying a passphrase or using a key.

Once they are decrypted, you can mount them as usual.  Then do an over-write if you so desire.

---

