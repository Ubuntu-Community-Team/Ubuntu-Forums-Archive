---
title: "access hard drive in xubuntu live usb"
date: 2012-03-11
forum: General Help
---

### Post by joeyjoejoejunior on 2012-03-11
Is there any way to access the files on my laptop's internal hard drive while running xubuntu 10.10 from a persistent live flash drive?
I don't see the hard drive in my 'places' folder.  I do see the hard drive in the 'search for files' dropdown menu, however I can't seem to search it.
any ideas?  it would be very nice to be able to access these files.

thanks

---

### Post by mastermesh on 2012-03-11
I had a similar problem... fixed it by putting ubuntu on the thumbdrive instead... and just installing to the hd from there.

---

### Post by joeyjoejoejunior on 2012-03-11
thanks mastermesh, but I think you've answered a different question for me.  I don't want to install xubuntu/ubuntu on the internal hard drive, I just want to be able to access files on that internal hard drive while running the persistent live OS installed on my usb flash thumb drive.  I have the persistent, live OS on the thumb drive all set up, I just can't get to the big hard drive on the laptop.
thanks anyhow, though

---

### Post by spiky001 on 2012-03-11
Hi  Did you mount your harddrive? Then cd into the mounted drive?

---

### Post by joeyjoejoejunior on 2012-03-11
> **spiky001 said:**
> Hi  Did you mount your harddrive? Then cd into the mounted drive?

I don't understand, do I need to mount the internal hard drive in order to access it?  Sorry if this is a silly question, I'm new to this.

Thanks

---

### Post by joeyjoejoejunior on 2012-03-11
by the way, the internal hard drive is fully functioning, with ubuntu instaled on it, if that means anything.

---

### Post by spiky001 on 2012-03-11
mkdir on usb at /mnt call it hdd run ```
 sudo fdisk -l
``` find the partition which you want  then run ```
sudo mount -v /dev/sdxx /mnt/hdd
``` change sdxx to the corresponding partition (sda1)or what ever it is.  Then cd /mnt/hdd should find your files

---

### Post by joeyjoejoejunior on 2012-03-11
Thank you, spiky, that worked perfectly.
This has to have been the fastest, most helpful experience I've had asking for guidance on a forum.  A new reason to to prefer ubuntu!

---

