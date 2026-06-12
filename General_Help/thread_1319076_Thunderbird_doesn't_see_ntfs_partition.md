---
title: "Thunderbird doesn't see ntfs partition"
date: 2009-11-08
forum: General Help
---

### Post by Steve Francis on 2009-11-08
My p.c. is configured to dual-boot into Windows XP or Ubuntu 9.04

I have all my Thunderbird data stored on a separate logical ntfs partition so that I can access my emails in either Ubuntu or XP.

The only way that Thunderbird will work on Ubuntu however is if I first go to Places - Computer and then double-click on the ntfs partition _before_ I start up Thunderbird.

If I don't do this, then Thunderbird starts but doesn't load my email archive.

How can I get Ubuntu to recognise the ntfs partition at boot up so that I don't have to go through the above procedure?

---

### Post by mac666 on 2009-11-08
have you mounted the partition before starting thunderbird? (e.g. explored the partition in natilus)

sudo aptitude update
sudo aptitude install ntfs-config
and run System > Storage Device manager. From their you can Automount the partition easly! (just click it and it will make config automatik)

---

### Post by Lateralis on 2009-11-08
To me it sounds like the NTFS partition isn't auto-mounting at startup.  This is quite normal, and easily changed. 

There are a couple of ways to do this, but both ways end up changing the same thing.  There is a file - /etc/fstab - whish is just about ubiquitous across all *nix systems.  It tells the operating system what discs you have, what file systems are on them and where you want them mounted.  To auto-mount your NTFS parition you have to edit this file.  You can either do it manually using an editor (Gedit, for example) or you can download a programme through the main repositories which will sort all this out for you!  I'll assume you would want to do the latter... :P  

Firstly, fire up a terminal (Applications->Accessories->Terminal) and type in the following:

```

sudo apt-get install ntfs-config

```

Once that has finished installing type 

```

sudo ntfs-config

```

into the command line.  It is probably a good idea to make sure that none of your NTFS partitions are mounted when you do this.  To unmount a drive, right-click on the Desktop shortcut for the drive and click "unmount".  

After typing in the above command you will get a pop-up GUI box.  First select all of the NTFS drives you want mounted at start-up, then click OK (or maybe next... I forget) and ensure that "enable write support for internal drives" is selected on the next screen.  Click OK and it should all be done!

---

### Post by The Funkbomb on 2009-11-08
Create a mount point and mount the drive using fstab.

First step, find the drive:

```
sudo fdisk -l
```

Find which one it is.  For the sake of this "how-to", we'll call it /dev/sda2

Next step is to make a mount point.

```
sudo mkdir /mnt/share
```

Now it's time to edit fstab.

```
sudo gedit /etc/fstab
```

Gedit pops open and you just need to add a line to the file and save it.

For this example, it would look something like this:

/dev/sda2  /mnt/share   ntfs  defaults,locale=en_US.utf8 0	0

The first one is the drive, then the mount point, the file system, the defaults, the dump and the pass.

Save the file and reboot.  Ubuntu should now mount that partition automatically and Thunderbird will connect.

---

### Post by Steve Francis on 2009-11-09
> **Lateralis said:**
> To me it sounds like the NTFS partition isn't auto-mounting at startup.  This is quite normal, and easily changed. 

There are a couple of ways to do this, but both ways end up changing the same thing.  There is a file - /etc/fstab - whish is just about ubiquitous across all *nix systems.  It tells the operating system what discs you have, what file systems are on them and where you want them mounted.  To auto-mount your NTFS parition you have to edit this file.  You can either do it manually using an editor (Gedit, for example) or you can download a programme through the main repositories which will sort all this out for you!  I'll assume you would want to do the latter... :P  

Firstly, fire up a terminal (Applications->Accessories->Terminal) and type in the following:

```

sudo apt-get install ntfs-config

```Once that has finished installing type 

```

sudo ntfs-config

```into the command line.  It is probably a good idea to make sure that none of your NTFS partitions are mounted when you do this.  To unmount a drive, right-click on the Desktop shortcut for the drive and click "unmount".  

After typing in the above command you will get a pop-up GUI box.  First select all of the NTFS drives you want mounted at start-up, then click OK (or maybe next... I forget) and ensure that "enable write support for internal drives" is selected on the next screen.  Click OK and it should all be done!


Thanks for your replies.

I chose the procedure suggested by Lateralis as I am a complete beginner.

It worked! This will save me the hassle of manually mounting the drives each time I boot up.

Appreciate the support, guys.

---

