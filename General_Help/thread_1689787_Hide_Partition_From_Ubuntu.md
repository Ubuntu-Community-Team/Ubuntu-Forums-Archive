---
title: "Hide Partition From Ubuntu"
date: 2011-02-17
forum: General Help
---

### Post by sunzeal on 2011-02-17
Hi

I have 1 Drive i.e Z:\ which is kept hidden in my Windows 7.

But its showing in Ubuntu as 250GB Partition.

I want to hide that drive from Ubuntu, how can i do that?

Please explain in details, this is first time i've been using Ubuntu.

---

### Post by Grenage on 2011-02-17
I presume that the partition is being listed in Nautilus (the file manager)?

The easiest way is to make a mount point, somewhere other than /media - I recommend /mnt:

```
sudo mkdir /mnt/*partitionx*
```

You can then add an entry for the drive in fstab (/etc/fstab.conf) that mounts the partition on the /mnt/partitionx directory.

If the drive was in the machine when you installed Ubuntu, then there may already be an entry for it.  If not, there are some great fstab guides on the web; post back if you have trouble.

---

### Post by ellgor on 2011-02-17
Hi,

You can use Gparted to do this, with Gparted running click on the appropiate partion (which will highlight it to show you the one you have chosen), from the options in the top bar select Partion and from the drop down select manage flags, in there is the option to hide.

Regards, Ellgor.

---

### Post by Kirboosy on 2011-02-17
[COLOR=Red]Welcome to the forums! :D[/COLOR]

Z:\....is that a networked drive or did you just randomly select Z as the drive letter?

gParted is what I would recommend. Its easier than modifying the fstab (which is intimidating for beginners)

---

### Post by sunzeal on 2011-02-17
yeah, those stuff are too complicated for me in Ubuntu.

@ caboos :-

i installed and extracted that software but idk how to run it.!

[IMG]http://lulzimg.com/i12/251808.pngt[/IMG]

---

### Post by Kirboosy on 2011-02-17
Open synaptic package manager (System-->Administration-->Synaptic)

Then type in the quick search box "gparted"

Mark the package for installation, then click the apply button. Let it download and install....

Once its done you should have a new item under System-->Admin-->GParted


Hope that helps. :)

---

### Post by sunzeal on 2011-02-17
@caboos :-

thanks man, i got it working, but the problem is that i cannot see any option to hide the disk.

Their is option called Unmount but it cannot be selected as it says disk is already in use :(

---

### Post by Kirboosy on 2011-02-18
Ok sorry it took me so long to get back to you...

Select the partition from gparted that you want to hide.

Then click Partition-->Manage Flags --> then check hidden.

You should be good to go then :D

---

