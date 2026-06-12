---
title: "How do I force a partition to mount?"
date: 2011-02-24
forum: General Help
---

### Post by listerdl on 2011-02-24
Hi [I posted this earlier]("http://ubuntuforums.org/showthread.php?t=1692843") but am not getting any replies so I hope you dont mind my slight variation to my question.

[COLOR="DarkGreen"]Is there a way to fix a partition that wont mount?[/COLOR]

When I boot into Ubunutu I am told that the shared partition (which I called Storage on my shared NTFS D Drive) wont mount.

IS there any way to fix this?

(Again apologies for my impatience but I am really keen to fix this - but my question does have a proposed variation)

Is this a good idea:

fsck /dev/sda1

---

### Post by drascus on 2011-02-24
have you tried to mount it with the command line and see what kind of error you get?

---

### Post by listerdl on 2011-02-24
Thanks for your reply - do you mean like this:

sudo mount -t ntfs-3g /dev/sda1 /media/Storage

? thanks again

---

### Post by seawolf167 on 2011-02-24
> **listerdl said:**
> sudo mount -t ntfs-3g /dev/sda1 /media/Storage

Yea, that command but without the type (since it should be able to automatically detect the type of NTFS, if it gives an error that might help explain some things). 

```
sudo mount /dev/sda1 /media/Storage
```

P.S. is /media/**S**torage capitalized on your file system (just to make sure since it's case sensitive)?

---

### Post by psusi on 2011-02-24
Since it is a Windows filesystem, you need to boot into Windows and have it run chkdsk.

---

### Post by listerdl on 2011-02-24
> **psusi said:**
> Since it is a Windows filesystem, you need to boot into Windows and have it run chkdsk.

After having run the chkdsk in windows, what would the next move be?

(Interestingly I have had many problems trying to do chkdsk - I think there has been some sort of massive crash....)

The machine boots fine into grub - no issues, a the windows partition works absolutely fine - just the windows ntfs/ shared hosting has gone AWOL

Any help GREATLY appreciated!!!!

---

### Post by psusi on 2011-02-24
> **listerdl said:**
> After having run the chkdsk in windows, what would the next move be?

Nothing.  Once Windows repairs the fs it will mount.

> **listerdl said:**
> (Interestingly I have had many problems trying to do chkdsk - I think there has been some sort of massive crash....)

What do you mean?  You might want to check the SMART status in the disk utility to make sure the drive is physically ok.  Make sure there are no reallocated, pending, or offline sectors.

---

