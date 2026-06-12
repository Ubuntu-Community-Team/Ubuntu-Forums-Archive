---
title: "can't write to new ext4 partition on external hdd"
date: 2009-11-22
forum: General Help
---

### Post by entropy1 on 2009-11-22
I have an external usb-connected hard drive.  It came formatted with NTFS.  I used GParted to shrink the ntfs partition in half and then formated the remaining unallocated space to ext4.  Now when I plug in the drive I cannot drag files to the ext4 partition - I get an error message saying "Permission denied".

What do I need to do so that I can copy files to the new ext4 partition?

---

### Post by Zoot7 on 2009-11-23
It's most likely that root has claimed ownership of the drive.
Get it back! ;)

Run this:
```
sudo chown -R $USER:$USER <Mount Point>
```
Where mountpoint is the directory where the drive is mounted. That'll make you the owner of the drive.

If you just want to add write permissions you could run:
```
sudo chmod -R +w <mount point>
```

---

### Post by entropy1 on 2009-11-23
Thank you, Zoot7.

Before I saw your post, I did something similar:
```

cd /media/mountpoint
sudo mkdir data
chown $USER:$USER data

```
Then I could put files in /media/mountpoint/data.

After I read your post, I noticed that the permissions for /media/mountpoint were drwxr-xr-x  (with group and owner both being root).  So I did
```

cd /media
sudo chmod go+w mountpoint/

```
Then I could put files in /media/mountpoint instead of /media/mountpoint/data.

---

### Post by Zoot7 on 2009-11-24
Good to hear you're sorted! :)

---

### Post by superfish2 on 2009-12-04
Thanks guys.  I just created a partition on my external hard drive also and was wondering why I couldn't paste to it.

A question.  If I take my hard disk and plug it into another computer, will this happen again or will it just work?

---

### Post by Zoot7 on 2009-12-04
> **superfish2 said:**
> Thanks guys.  I just created a partition on my external hard drive also and was wondering why I couldn't paste to it.

A question.  If I take my hard disk and plug it into another computer, will this happen again or will it just work?
It should work okay afaik. 
But if you wanted to 100% sure you could always just set the permissions so that there's no restriction, ie do:
```
sudo chmod -R 777 <mount point>
```

Just be careful that you specify the mountpoint correctly there, because using that command like that can be quite detrimental if you change the permissions in the wrong place.

---

### Post by sirajperson on 2010-03-07
Thanks guys, this really helped[.]("http://sirajspot.com") :D

---

### Post by zwimox on 2010-03-18
Thanks! I was struggling for hours trying to figure it out :P

---

### Post by tahitiwibble on 2010-05-20
Oops, sorry, wrong thread.

---

### Post by JakcV on 2010-12-25
Finally, I found the solution. I struggle to backup my document into the external hard disk using nautilus, have to through the console with root permission. 
just can't think of changing the ownership of the folder. haha

---

