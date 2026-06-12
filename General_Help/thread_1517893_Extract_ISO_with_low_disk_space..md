---
title: "Extract ISO with low disk space."
date: 2010-06-25
forum: General Help
---

### Post by zmpeg on 2010-06-25
Hi, First post here. I've done a lot of searching but can't find anything like this.

I've got a slicehost VPS with 10GB disk space, and I'm trying to extract a 6.4gb ISO file. Between the ISO and the OS i've got just 761MB to play with. Is there anyway to extract files from within the ISO without needing another 6.4gb?

I've tried mounting the ISO as read/write so I could move files instead of copy, but did not have any luck. See [here]("http://www.linuxquestions.org/questions/linux-general-1/mount-iso-writable-227493/#post3299779") and [here]("http://ubuntuforums.org/showthread.php?t=52255").


Should I just give up, download the iso, then re-upload the files? 6.4gb represents a long time over dsl.

Thanks.

---

### Post by dasy2k1 on 2010-06-25
burn the iso to a DVD then copy the files off?

---

### Post by bodhi.zazen on 2010-06-25
> **zmpeg said:**
> Hi, First post here. I've done a lot of searching but can't find anything like this.

I've got a slicehost VPS with 10GB disk space, and I'm trying to extract a 6.4gb ISO file. Between the ISO and the OS i've got just 761MB to play with. Is there anyway to extract files from within the ISO without needing another 6.4gb?

You will need at least 6.4 Gb and probably more space then that.

> I've tried mounting the ISO as read/write so I could move files instead of copy, but did not have any luck. See [here]("http://www.linuxquestions.org/questions/linux-general-1/mount-iso-writable-227493/#post3299779") and [here]("http://ubuntuforums.org/showthread.php?t=52255").

Those threads are old, are they your threads ?


> Should I just give up, download the iso, then re-upload the files? 6.4gb represents a long time over dsl.

Thanks.

What is it exactly you are wanting to modify on the iso image ?

---

### Post by zmpeg on 2010-06-25
Hi, Thanks for your help.

Those are not my threads (found on Google). I was thinking I could move the files out of the ISO image, thereby decreasing the size of the ISO while writing to disc.

The ISO is Call of Duty 4. The end goal is to setup a server. To install the server, you need some files off the disc (/Setup/Data) and some files from the internet. I've uploaded the disc. But now hit this wall. I'd rather not repeat uploading the actual files (which I should have done off the bat).

UPDATE: I should probably mention I own the game, but because my DSL line tops out at 50KB/Sec upload I used a torrent to get it to the VPS, which D/L'd at over 1MB/Sec.

---

### Post by zmpeg on 2010-06-25
> **dasy2k1 said:**
> burn the iso to a DVD then copy the files off?

That's not the issue.. I could mount the ISO and copy the files, saving a DVD.

---

### Post by dcstar on 2010-06-25
> **zmpeg said:**
> Hi, First post here. I've done a lot of searching but can't find anything like this.

I've got a slicehost VPS with 10GB disk space, and I'm trying to extract a 6.4gb ISO file. Between the ISO and the OS i've got just 761MB to play with. Is there anyway to extract files from within the ISO without needing another 6.4gb?

I've tried mounting the ISO as read/write so I could move files instead of copy, but did not have any luck.
........

There is no point mounting ISOs as RW, as they are embedded images that need to be specifically created.

ISOs are automatically available to be used by the Archive Manager so there is no need to "mount" anything if you want to extract files from them.

---

### Post by zmpeg on 2010-06-25
> **dcstar said:**
> There is no point mounting ISOs as RW, as they are embedded images that need to be specifically created.

ISOs are automatically available to be used by the Archive Manager so there is no need to "mount" anything if you want to extract files from them.

Thanks for explaining ISOs. Part of the problem is this is Ubuntu Server VPS, I don't have a window manager.. CLI only.

---

### Post by Bachstelze on 2010-06-25
Mount the ISO on hour home computer, and upload the individual files you need. That's probably the only way.

---

### Post by zmpeg on 2010-06-25
Eh, I was hoping to avoid that. Oh well.

Thanks everyone.

---

### Post by dcstar on 2010-06-26
> **zmpeg said:**
> Thanks for explaining ISOs. Part of the problem is this is Ubuntu Server VPS, I don't have a window manager.. CLI only.

Then you can mount the ISO using the "loop" option and then extract whatever you need:

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

