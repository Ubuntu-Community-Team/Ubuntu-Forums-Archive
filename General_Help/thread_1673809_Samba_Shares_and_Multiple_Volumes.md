---
title: "Samba Shares and Multiple Volumes"
date: 2011-01-23
forum: General Help
---

### Post by Kissell on 2011-01-23
So, I have an encrypted volume on a software raid, and it is shared with samba (i know, i know, the encryption is only protecting it when it's powered off or the volume is locked), but anyway, this served my needs very well.

Unfortunately, I ran out of space, and rather than extend the raid with more disks of a small size and increasing the risk of multi-disk failture...  I decided to create a new volume using larger disks.  The new volume isn't large enough to replace the old volume, just large enough to move some of the data to relieve capacity.

Anyway, I built the new volume and moved the data...  now I have two encrypted volumes.  But I can't get the new volume to show up inside the existing samba share.  I want to be able to go to a mapped drive from a windows client and see everything like I used to, in one place, all on the same drive.  

Solution #1: I could mount the new volume inside the old volume...  however, I really need this to be able to be opened by a monkey from the GUI, and by default the GUI mounts encrypted volumes in the /media folder.

Solution #2: I created a symbolic link...  this seemed to work, it works locally on the ubuntu server...  however, from a windows client it says "access denied" when I try to go to the folder that is the symbolic link, even though I've checked and re-applied the same permissions all the other folders have.  NOTE: From a ubuntu client, the folder of the new volume doesn't even show up in the network share.

---

### Post by Don Barzini on 2011-01-23
Try this....

[http://ubuntuforums.org/showpost.php?p=4095531&postcount=10](http://ubuntuforums.org/showpost.php?p=4095531&postcount=10)

Then **restart** your Samba service on the server.

**EDIT**....

It appears that some syntax may have changed. The correct syntax for the **smb.conf** file in the GLOBAL section may now be....

```
follow symlinks = yes
**wide links** = yes
unix extensions = no
```

Then restart the Samba service.

See if that works.

---

### Post by Kissell on 2011-01-23
That sounded promising, but no luck.  I even rebooted just to be sure, but no change.


EDIT: Oh, maybe the correct syntax will work.  :)
I'll give that a try tomorrow.

---

### Post by Kissell on 2011-01-24
Ah!  It worked!  

It's been a few years since I've used Linux, it's all slowly coming back to me, with the help of this forum.

Thanks so much!

---

