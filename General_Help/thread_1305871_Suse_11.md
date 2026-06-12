---
title: "Suse 11"
date: 2009-10-30
forum: General Help
---

### Post by cowboy7305 on 2009-10-30
I have downloaded linux suse 11.1 the dvd version and i would like to have a look at it
i have ubuntu 9.1 installed  can any one help me if i can use side by side on same hard drive
many thanks

---

### Post by mechro on 2009-10-30
Yes you can depending on the size of the hard drive.

You'll have to find out from Suse whether its installer will make room (partition creation/resizing) for both Suse and Ubuntu. If it doesn't then you'll have to use a tool like gparted from Ubuntu and then install Suse.

---

### Post by olepi on 2009-10-30
As a forewarning, everytime I've installed Suse 11.1, it has blown away my ubuntu boot loader. I'm not sure whether the error is on my part or Suse's.  Just make sure you have a plan when you're finished with the Suse 11 installation and find you cannot immediately boot into Ubuntu.  I usually install Suse first but I'm sure there's a better way.

---

### Post by mechro on 2009-10-30
> **olepi said:**
> As a forewarning, everytime I've installed Suse 11.1, it has blown away my ubuntu boot loader. I'm not sure whether the error is on my part or Suse's.  Just make sure you have a plan when you're finished with the Suse 11 installation and find you cannot immediately boot into Ubuntu.  I usually install Suse first but I'm sure there's a better way.

I assume they'd use grub and pick up other operating systems, but perhaps not?

---

### Post by Barafu Albino Cheetah on 2009-10-30
Suse installs it's bootloader without asking at all. You will have to reinstall ubuntu's bootloader or add Ubuntu to Suse's. 

If you want only to look at it, try VirtualBox instead. It is the safest way.

---

### Post by olepi on 2009-10-30
Every time I've installed Suse 11.1, it never picked up my existing Ubuntu installation - not sure why. I was using ext4 with Ubuntu but I'm not sure whether that would make a difference or not.

---

### Post by cowboy7305 on 2009-10-30
thanks for that info 
i did try loading suse and got to the part of installing  but like others it did not seem to find ubuntu and looked like it wanted to use all hard drive ,so will give it a miss, iam not that good with any thing that is out of the ordinary 
but i do like looking

---

### Post by jrrader on 2009-10-30
+1 Virtualbox

SUSE installer is probably one of the most unpleasant I've dealt with.  Possibly a tie with Solaris.  There are ways to label partitions, but it's not as straight forward as the ubuntu installer.

---

