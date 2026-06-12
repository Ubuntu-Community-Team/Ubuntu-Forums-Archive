---
title: "Where is my original /home when using Live CD?"
date: 2010-02-03
forum: General Help
---

### Post by jripple on 2010-02-03
Installed karmic fresh a couple weeks ago.

After doing the last update I can only reboot to the BusyBox (intramfs) prompt -pic is attached.  Other posts suggest there are some missing modules but I haven't figured it out yet.

There are some files I'd like to save to my external hard drive not to mention my evolution emails, Firefox bookmarks, etc. in case I have to reinstall 9.10.

Can any one help me find these things when I'm booted up using the Live CD?  They must be buried somewhere in the file system but haven't been able to find them.

Also, if anyone wants to suggest how to get past the BusyBox boot issue, attached is the RESULTS.txt file from the Boot Info Script.

-Hopefully awaiting your help . . .

Thanks,
JR

---

### Post by cjhabs on 2010-02-03
All Evolution files are held under .evolution in your home folder.
All Firefox files are held in .mozilla/firefox in your home folder.

Your home folder is typically a sub-folder under /home
I make /home a separate partition so that it doesn't have to be wiped out when installing the OS.

Chris

---

### Post by nothingspecial on 2010-02-03
```
sudo fdisk -l
```

from the output find out which partition is your ubuntu partition.

```
sudo mkdir /media/buntu
```

```
sudo mount -t ext3 /dev/sd?? /media/buntu
```

change ext3 to ext4 if necessary and replace the question marks with the correct letter and number you found out from the first command.

```
cd /media/buntu/home/username
```

your there.

---

### Post by Dru89 on 2010-02-03
You may also find it just as easily under the "Places" section as a drive to look into.  If you have your /home drive as a separate partition, you'll find it there.  Otherwise it should be with your regular / (root) partition.

---

### Post by jripple on 2010-02-03
> **cjhabs said:**
> Your home folder is typically a sub-folder under /home


Thanks Chris,

I know that's usually the case under normal booting conditions.  However, when I boot using the Live CD the user is "ubuntu".  The file browser shows /home as having one subdirectory: ubuntu.  I've hunted around but haven't been able to find a dir that contains my stuff.  It's got to be buried in some other part of the file system.

---

### Post by jripple on 2010-02-03
That worked like magic!  Thanks.

One thing,  all the folders are unavailable.  When I try to open them I get this message:
The folder contents could not be displayed.  You do not have the permissions necessary to view the contents of "foldername".

That's probably because having booted to the live cd, the default user is "ubuntu".  What's the best way to proceed from here?

Thanks,
J.

---

### Post by QuimNuss on 2010-02-03
Though not very advisable, you can always run sudo nautilus on a terminal...

---

### Post by garvinrick4 on 2010-02-03
In Live CD mount the partition you want in Places dropdown menu. Then Alt/F2 type in
gksudo nautilus then there will be root on top of list. Open your partition in that same list
and you will be root and have its priveledges. You can do the same thing from Terminal if
you desire. Study the chroot command while in terminal of Live CD. Or post in thread and you
will get desired instructions. But if you google you will find easy enough.

---

### Post by jripple on 2010-02-03
Thanks everyone, this was very useful information and provided everything I needed.

J.

---

### Post by jripple on 2010-02-03
If I copy the .evolution folder to my external drive and then use it to replace the one that is created upon reinstalling karmic, will it work straight across?

---

