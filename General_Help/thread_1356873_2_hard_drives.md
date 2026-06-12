---
title: "2 hard drives"
date: 2009-12-16
forum: General Help
---

### Post by klnyc on 2009-12-16
Hi folks,

  Very newbie here..Okay, lets get down to the question.
I redid the Ubuntu server..basically it was an old Vista rig.
Okay, the primary HD is where my Ubuntu installed.  On my 2nd HD which is a 200gig data drive that I have music and pics in there.
How do I make my linux box to see or mount my 2ndry drive?

Thanks for help guys!

k

---

### Post by ean5533 on 2009-12-16
> **klnyc said:**
> Hi folks,

  Very newbie here..Okay, lets get down to the question.
I redid the Ubuntu server..basically it was an old Vista rig.
Okay, the primary HD is where my Ubuntu installed.  On my 2nd HD which is a 200gig data drive that I have music and pics in there.
How do I make my linux box to see or mount my 2ndry drive?

Thanks for help guys!

k

You're using Ubuntu server, so are you using the command line only, or do you have a graphical interface to work with? 

Don't worry, we can help either way. :)

---

### Post by SuperSonic4 on 2009-12-16
It should be 'loaded' on boot although it won't mount unless you explicitly tell it to. As you have the server edition I'm guessing you don't have a GUI? (CLI is simple enough to action anyway)

Plug the second drive in and post the output of ```
sudo fdisk -l
```

---

### Post by klnyc on 2009-12-16
> **ean5533 said:**
> You're using Ubuntu server, so are you using the command line only, or do you have a graphical interface to work with? 

Don't worry, we can help either way. :)

CLI Im using :)  Im going try learn the hard way.

---

### Post by klnyc on 2009-12-16
> **SuperSonic4 said:**
> It should be 'loaded' on boot although it won't mount unless you explicitly tell it to. As you have the server edition I'm guessing you don't have a GUI? (CLI is simple enough to action anyway)

Plug the second drive in and post the output of ```
sudo fdisk -l
```


Thanks for the fast reply.  I'm gong try it and report back.

---

### Post by SuperSonic4 on 2009-12-16
> **klnyc said:**
> CLI Im using :)  Im going try learn the hard way.

Some of us find CLI easier ;) still takes a while to get used to links xD

---

### Post by klnyc on 2009-12-16
> **SuperSonic4 said:**
> Some of us find CLI easier ;) still takes a while to get used to links xD

Okay, this what I see when I do "sudo fdisk -1"  without the quotes.
/dev/sdb1               1        3738    30025453+   7  HPFS/NTFS

Is this correct command?
```
sudo mount /dev/sb1

```

---

### Post by ean5533 on 2009-12-16
> **klnyc said:**
> Okay, this what I see when I do "sudo fdisk -1"  without the quotes.
/dev/sdb1               1        3738    30025453+   7  HPFS/NTFS

Is this correct command?
```
sudo mount /dev/sb1

```

Close -- you also have to tell it where to mount to. You can mount it to almost anywhere, but typically other drives or partitions are mounted to /media/SOMEFOLDER. You need to create this folder before you can mount to it. So, for example...

```
sudo mkdir /media/mystuff
sudo mount /dev/sdb1 /media/mystuff
```

---

### Post by klnyc on 2009-12-16
> **ean5533 said:**
> Close -- you also have to tell it where to mount to. You can mount it to almost anywhere, but typically other drives or partitions are mounted to /media/SOMEFOLDER. You need to create this folder before you can mount to it. So, for example...

```
sudo mkdir /media/mystuff
sudo mount /dev/sdb1 /media/mystuff
```

Hah, I mounted by mistake.. I mounted on the /mnt folder. Thats okay, at least I know where is at.  
I want to mount in my own home folder next time.

Another question:

How do I make, so it auto mount when the server it reboot?
It would be PITA, every time you tp have manual mount the drive :(

thanks again for the help you guys.. I'm sure there's more I need to ask.  Thanks again guys.

---

### Post by baddog144 on 2009-12-16
You have to edit /etc/fstab/ 
and add something like this:
```
/dev/sdb1 /media/stuff ntfs defaults 0 1
```
That might not be quite right, but I hope it's close :)

---

### Post by ean5533 on 2009-12-16
> **klnyc said:**
> How do I make, so it auto mount when the server it reboot?

The file /etc/fstab lists partitions to automount on startup. So, open'er up for editing with this command:

```
sudo gedit /etc/fstab
```

Then add a line to the bottom that looks something like the following:

```
/dev/sdb1       /media/disk 	ext3 	rw,nosuid,nodev
```

The first path is the device you're mounting, the second path is the folder you're mounting to. "ext3" is the filesystem type (you might have used ext4 or something else). The last three comma-separated parameters are special flags that I won't go into because they're a bit complicated.

Hope I didn't over-explain that. :)

**Edit:**** Just realized that I'm dumb and you already told us that the disk is formatted as NTFS, not ext3. You still need to edit /etc/fstab, but baddog144's line will work better than mine. :)**

---

### Post by klnyc on 2009-12-16
> **ean5533 said:**
> The file /etc/fstab lists partitions to automount on startup. So, open'er up for editing with this command:

```
sudo gedit /etc/fstab
```

Then add a line to the bottom that looks something like the following:

```
/dev/sdb1       /media/disk 	ext3 	rw,nosuid,nodev
```

The first path is the device you're mounting, the second path is the folder you're mounting to. "ext3" is the filesystem type (you might have used ext4 or something else). The last three comma-separated parameters are special flags that I won't go into because they're a bit complicated.

Hope I didn't over-explain that. :)

**Edit:**** Just realized that I'm dumb and you already told us that the disk is formatted as NTFS, not ext3. You still need to edit /etc/fstab, but baddog144's line will work better than mine. :)**

:) Okay, I give a shot now and report back to you tomorrow morning.    Next step is I want to WRITE on NFTS from Linux.

---

### Post by PseudoLemon on 2009-12-16
Type in ```
sudo apt-get install ntfsprogs
```
That'll basically give you full read/write access.

---

### Post by SuperSonic4 on 2009-12-17
ntfs-3g is also meant to be better than ntfs

```
sudo apt-get install ntfs-3g
```

Don't use gedit - it will get you nowhere on a CLI- instead use nano (or vi) designed for the CLI


```
sudo nano /etc/fstab
```

Add the following line, note that you must use the full path to your home directory for it to mount there. When editing fstab:

```
disk   mnt_dir   filesystem   options  dump  pass
```

```
/dev/sdb1 /home/user/media ntfs-3g defaults 0 0
```

Change the 0 to a 2 if you want a fsck every boot

---

