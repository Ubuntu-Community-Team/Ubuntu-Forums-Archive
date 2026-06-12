---
title: "How to install back Windows? What's NTFS?"
date: 2010-04-10
forum: General Help
---

### Post by sincerelyydavid on 2010-04-10
So i'm trying to wipe off ubuntu and install back windows. when i tried to do a fresh installation of windows 7, i ran into some sort of partition problem, and it said that windows cannot be installed because it's not a NTFS partition or Something. how can i fix this?

---

### Post by Klump on 2010-04-10
Well, if you want to completely erase Ubuntu and install Windows I assume you no longer need that partition, do you? :) You can delete that partition and create a new one with Windows 7 installer.

---

### Post by pickarooney on 2010-04-10
NTFS is a Windows-style file system. You'll need to format that partition with this filesystem in order to be able to install Windows. I've no idea if Windows 7 provides a tool to do this.

---

### Post by Monotoko on 2010-04-10
there should be a link saying "Advance" or some similar thing when it tells you it cannot install to that partition, click that, then delete the partition and install Windows to the "unpartitioned space"

Windows will know what to do and restore it to NTFS for you :)

---

### Post by Slim Odds on 2010-04-10
> **pickarooney said:**
> NTFS is a Windows-style file system. You'll need to format that partition with this filesystem in order to be able to install Windows. I've no idea if Windows 7 provides a tool to do this.

Are you serious?

You think that Windows 7 doesn't come with a tool to create it's own default partitions?

---

### Post by Klump on 2010-04-10
No need to mock people :) Maybe he meant tool with a GUI because as far as I remember, it comes only with command line one.

---

### Post by DrMelon on 2010-04-10
> **Klump said:**
> No need to mock people :) Maybe he meant tool with a GUI because as far as I remember, it comes only with command line one.

It has a basic, extended-ASCII GUI :KS

---

### Post by Georules on 2010-04-10
The windows installer will have an option to delete the partition and reformat it with NTFS.  This option likely is given to you when you see the error about the partition.  

Keep in mind all of your files will be GONE.

---

### Post by Slim Odds on 2010-04-10
> **Klump said:**
> No need to mock people :) Maybe he meant tool with a GUI because as far as I remember, it comes only with command line one.

I'm not a mind reader. What was written made no sense.

---

### Post by Klump on 2010-04-10
> **Slim Odds said:**
> I'm not a mind reader. What was written made no sense.

Well, he didn't say Windows does **not** provide a tool. He said he didn't know that so that's quite clear for me :)

---

