---
title: "mount /media/sdc1 &lt;---how do i avoid this?"
date: 2009-09-28
forum: General Help
---

### Post by sponsoredwalk on 2009-09-28
**[COLOR="Red"]Hi, every time I connect a phone or usb key to my pc via the usb slots I must go through the same motions;[/COLOR] **

>  # mount /media/sdc1
[mntent]: line 13 in /etc/fstab is bad
# mount /media/sdd1
[mntent]: line 13 in /etc/fstab is bad
mount: special device /dev/sdd1 does not exist
 
>>>> **[COLOR="Red"]So I take out the usb, re-insert it and do this;[/COLOR] **

#  mount /media/sdd1
[mntent]: line 13 in /etc/fstab is bad

>>>> Before I can access the usb/phone I must take it out again and 
re-insert it.

**[COLOR="Red"]Is there anyway to bypass this nonsense? To make it automatically detectable?[/COLOR] **

---

### Post by falconindy on 2009-09-28
Assuming you're on Ubuntu (and not a variant like Kubuntu), the package 'gnome-volume-manager' should be making sure that removable devices are being mounted/unmounted properly when they're connected. You don't need to be messing around with /etc/fstab for that.

---

### Post by sponsoredwalk on 2009-09-28
I'm on Ubuntu. I Just go into >>terminal and type;
> #su
(password)
#mount /media/sdc1
etc... Does this mean it's broken? If so is it possible to fix?

---

### Post by falconindy on 2009-09-28
So is gnome-volume-manager installed? I accidentally uninstalled it once when I was trying to be efficient... didn't notice it for a while...

If g-v-m is installed, then you may have a problem with FUSE.

---

### Post by sponsoredwalk on 2009-10-05
gnome-volume-manager is installed, and I installed some of the mount programs that came up in synaptic when i typed in fuse and now, the volume detects but I get a mssage saying 

"Cannot mount  Volume - You do not have permission to mount this volume"

How do I gain permissions and permanently change them to allow it to automatically work?

---

### Post by sponsoredwalk on 2009-10-05
Got it!I went to my fstb and deleted two lines that I think I had to put in over a year ago due to a problem back then and now it works. Thanks a million!

---

