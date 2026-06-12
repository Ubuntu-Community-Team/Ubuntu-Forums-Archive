---
title: "I know you can &quot;dd&quot; disk to disk. But what about disk to folder?"
date: 2011-08-14
forum: General Help
---

### Post by Roasted on 2011-08-14
So, I have a ton of hard drive space in my desktop. That said, I was curious about something. I plan to get a 32gb micro SD card for my phone. It'll be partitioned off because my Android will use a 2gb ext3 partition on it for extra application storage, and the 30gb fat32 will be for media.

So I got to wondering... I COULD get a 2nd 32gb micro SD card and "dd" them so I have a direct backup. But what about dd'ing to a file to keep on my computer? That way if my micro SD card ever gets lost or dies, I can just "dd" from the file on my computer to the new micro SD card I would get. Of course, it would be the same brand, size, class, etc.

Is it possible to "dd" a disk to a folder on a computer? Or somehow compress it to a tarball and later extract if I decide to pull it back off?

---

### Post by HermanAB on 2011-08-14
Howdy,

Yes, you can specify a filename as the 'of' (output file).

dd if=/dev/sda of=/home/joesoap/filename.img

(provided that it is on a different physical disk!)

---

### Post by Roasted on 2011-08-14
> **HermanAB said:**
> Howdy,

Yes, you can specify a filename as the 'of' (output file).

dd if=/dev/sda of=/home/joesoap/filename.img

(provided that it is on a different physical disk!)

Hmm... I assume that's what Clonezilla LiveCD does when you choose DD? After all it uses .img extension. Guess I never thought about that.

Is the same true in reverse when I restore it?

dd if=/home/joesoap/filename.img of=/dev/sda


??

Appreciate your quick answer! :guitar:

---

### Post by idoitprone on 2011-08-14
> **Roasted said:**
> Hmm... I assume that's what Clonezilla LiveCD does when you choose DD? After all it uses .img extension. Guess I never thought about that.

Is the same true in reverse when I restore it?

dd if=/home/joesoap/filename.img of=/dev/sda


??

Appreciate your quick answer! :guitar:
yep, but clonezille is usually prefered since it only copies the bytes that has been used rather then the whole drive including unused space

---

