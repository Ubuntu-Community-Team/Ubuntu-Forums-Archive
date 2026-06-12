---
title: "Windows partition won't mount automatically at startup"
date: 2010-06-02
forum: General Help
---

### Post by ieee488 on 2010-06-02
I had to re-install Windows XP because the install was running slow.

So, I created another partition using GParted for my personal data and moved my files there and re-installed Windows XP.

Now, the Windows partition won't mount automatically.

NTFS Configuration Tool shows 0.0GB. So, I have to open up a Terminal window, and issue **sudo mount /dev/sda1 /media/Windows** and everything is fine.

What is wrong?  How do I fix this?

---

### Post by ieee488 on 2010-06-02
Answering my own post.

There were two entries in my /etc/fstab file for the Windows partition. I commented out the "wrong" one and now the automounting is working again.

---

### Post by dcstar on 2010-06-03
> **ieee488 said:**
> Answering my own post.

There were two entries in my /etc/fstab file for the Windows partition. I commented out the "wrong" one and now the automounting is working again.

Then mark the thread.

---

