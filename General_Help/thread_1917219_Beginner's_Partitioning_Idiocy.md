---
title: "Beginner's Partitioning Idiocy"
date: 2012-01-29
forum: General Help
---

### Post by iangarforth on 2012-01-29
Thing is, I knew before I started that careful planning was important...

I've made what I believe is called in the trade, a bugger's muddle of this.

On my MSI Wind U135 netbook, it had Windows 7 installed across the whole 160GB hard drive.

Most of my files are in Dropbox, but a whole chunk of my stuff is photos, which I run through Picasa, and it's just too meaty to run in the cloud.

Now, in the meantime, I'm got used to Ubuntu, and am loving it.  I can, of course, mount my other hard drive, and copy files, but I now think I've got it all set up totally wrong.

At the moment, GParted shows that I have:

[10GB Bios Recovery][100MB NTFS Windows Boot][125GB Windows][2GB Swap][12GB Linux]

What I guess would be way better if it went:

[10GB Bios Recovery][100MB NTFS Windows Boot][25GB Windows][2GB Swap][25GB Linux][88GB NTFS Files inc photos]

Even better would be if I could mount the final partition automatically when Ubuntu boots, so that Picasa runs natively in Linux, drawing the files from the other partition, and I can access my 'Files' partition from either windows or Ubuntu.

Is it too late to do this?  Can I resize, shrink and move the partitions at this stage?

Cheers

---

### Post by lechien73 on 2012-01-29
Hi...The good news is - it's not too late!! You can dynamically resize partitions...the best thing to do would be to download the GParted live CD/USB from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and boot from that. Since you can't modify a mounted partition.

I'm guessing that at least one or two of those partitions may be in an extended partition, in which case, resizing could take a lot of time, and I'd make sure you have full backup before you start.

It would be a good idea to read up about partitioning before you start, so you know what you're getting yourself into. These resources might help:

[http://gparted.sourceforge.net/display-doc.php?name=help-manual](http://gparted.sourceforge.net/display-doc.php?name=help-manual)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

There are also a few guides showing how GParted works.

---

### Post by iangarforth on 2012-02-07
Thanks for that.  I used the GParted Live CD - what an awesome bit of software!  It wasn't even as slow as I feared, and everything went swimmingly, with no problems booting into either partition.

The only fly in the ointment is that when I now boot into Ubuntu, I get an error message on the splash screen that says:

[B]The disk drive for UUID=blah blah is not yet ready or present

Wait to continue, press M to mount or S to skip[/B]

I presume it's looking for the CD drive that I ran the Gparted from, but though it goes past this and boots fine, it's a mild annoyance that I'd like to get rid of if I can.

Any ideas?

---

### Post by plucky on 2012-02-07
> **iangarforth said:**
> Thanks for that.  I used the GParted Live CD - what an awesome bit of software!  It wasn't even as slow as I feared, and everything went swimmingly, with no problems booting into either partition.

The only fly in the ointment is that when I now boot into Ubuntu, I get an error message on the splash screen that says:

[B]The disk drive for UUID=blah blah is not yet ready or present

Wait to continue, press M to mount or S to skip[/B]

I presume it's looking for the CD drive that I ran the Gparted from, but though it goes past this and boots fine, it's a mild annoyance that I'd like to get rid of if I can.

Any ideas?

More likely is that the UUID of one of your partitions has changed as you resized them.

Open a terminal and compare the UUID's given with the commands ```
cat /etc/fstab
sudo blkid
``` and change the ones that don't match the "sudo blkid" command in the /etc/fstab file.

Or post the outputs to the forum.

Good Luck

---

### Post by iangarforth on 2012-02-07
Ok, so the offending partition is the swap file partition.  I can swap the UUID for the correct one in Gedit, but it then won't let me save the file as it's read only, and I'm not sure how to change the permissions..?

---

### Post by plucky on 2012-02-07
> **iangarforth said:**
> Ok, so the offending partition is the swap file partition.  I can swap the UUID for the correct one in Gedit, but it then won't let me save the file as it's read only, and I'm not sure how to change the permissions..?

Try ```
gksudo gedit /etc/fstab
```

Good luck

---

### Post by dragonfly41 on 2012-02-07
re: your earlier question about sharing folders between windows and ubuntu this recent thread seems relevant ..

[http://ubuntuforums.org/showthread.php?t=1648219&page=2](http://ubuntuforums.org/showthread.php?t=1648219&page=2)

---

### Post by iangarforth on 2012-02-07
> **plucky said:**
> Try ```
gksudo gedit /etc/fstab
```

Good luck

Sorted.  Nice one.

Thanks to all for their input and help!

---

### Post by iangarforth on 2012-02-07
Oh, and thanks, Dragonfly - have just realised the power of what you referred me to!

---

