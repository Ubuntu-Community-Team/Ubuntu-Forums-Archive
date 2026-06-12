---
title: "GParted Partition Resizing Help"
date: 2010-03-06
forum: General Help
---

### Post by ushpiy on 2010-03-06
Hello, all!

I have a NTFS drive of 195 GB and another unallocated drive of space 50 GB. I want to merge them.
I am not able to so since I think they are not contiguous. I want to make them contiguous so to merge them.
So guys please help me to make it contiguous to be able to merge the two drives.

I am using the latest version of GParted Live CD.

My situation is similar to this
[http://ubuntuforums.org/archive/index.php/t-1098920.html](http://ubuntuforums.org/archive/index.php/t-1098920.html)

I am running Windows 7 x64.
Thanks

---

### Post by cong06 on 2010-03-06
Um. Just to know exactly what's going on, could you open up your terminal (start > accessories > gnome-terminal)
and type in:
```

fdisk -l

```

And then paste the output here.

---

### Post by ushpiy on 2010-03-06
Here's an image of the output
[http://xs.to/image-A4F1_4B92710C.jpg](http://xs.to/image-A4F1_4B92710C.jpg)

---

### Post by digitalhead on 2010-03-06
Note that GPartEd itself cannot resize Windows Vista or newer NTFS partitions, or at least shouldn't. See the Info dialog. (desktop > Info > Windows)

---

### Post by ushpiy on 2010-03-06
Well I'll admit I'm a newbie and well could you please explain it and a possible solution (if applicable) for it.

---

### Post by digitalhead on 2010-03-06
You might want to take a look at this:
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

It does use GPartEd directly, but it also explains how to fix the possible mess afterwards, though it requires the Windows install disk (not the OEM restore).

---

### Post by MooPi on 2010-03-06
If I'm not mistaken Windows 7 comes with a disk utility . You may want to check that out first.

---

### Post by digitalhead on 2010-03-06
> **MooPi said:**
> If I'm not mistaken Windows 7 comes with a disk utility . You may want to check that out first.

That's good information to have. I haven't touched a Windows 7 computer and have barely touched any Windows computer at all for the past few years.

---

### Post by ushpiy on 2010-03-06
@digitalhead
> You might want to take a look at this:
[http://www.howtogeek.com/howto/windo...sta-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")
It does use GPartEd directly, but it also explains how to fix the  possible mess afterwards, though it requires the Windows install disk  (not the OEM restore).I dont really understand how it would help since I am not able to merge/resize.
The error would occur after the resize would have taken place but I am not able to merge/resize it in the first place.
This is what i understood from the link if you mean something else then please be kind enough to enlighten me.

@MooPi and digitalhead
Yeah but the extend option is greyed out and that's why I am depending on Gparted.

The reason both are not able to expand the operation (according to me, maybe I'm wrong) is due to the contiguous space thing.
I want to resolve that.

---

### Post by ushpiy on 2010-03-06
bump

---

### Post by digitalhead on 2010-03-07
Could you take a screenshot of what GPartEd shows for the drive?

---

### Post by cong06 on 2010-03-08
Sorry about that. The info you posted hlped, and I'm sure these other guys helped too.
Just to add my two cents (that term is so weird):

What I would try to do is open up gparted (from your cd).
Go to "View" and "File System Support"

You'll get a chart that lists all the different formats, and mentions it's compatibility.
NTFS will probably have a row of Red X's. If not, then you should be good to go with it.
If it does, then try and open up a terminal and run: "sudo apt-get install ntfsprogs"

Now, you're not running off an install, but It should still mange (as far as I know) to download the application and install it in memory.
If it succeeds, open up "File System Support" and see if it's available.

Disclaimer: I have no idea how that live system works for the gparted Live Disk.

---

### Post by ushpiy on 2010-03-08
Thanks but I am not interested in continuing that operation as a new error has struck me.
I have made a new thread for it.
[http://ubuntuforums.org/showthread.php?p=8933951#post8933951](http://ubuntuforums.org/showthread.php?p=8933951#post8933951)

EDIT: I have resolved this issue.

---

