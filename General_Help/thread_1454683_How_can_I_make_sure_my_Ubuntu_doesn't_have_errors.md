---
title: "How can I make sure my Ubuntu doesn't have errors?"
date: 2010-04-15
forum: General Help
---

### Post by TheNerdAL on 2010-04-15
So I think I deleted something important but I am not sure and would like to know if there is some way I can make sure my Ubuntu doesn't have error or anything, thanks.

---

### Post by Carl Hamlin on 2010-04-15
> **TheNerdAL said:**
> So I think I deleted something important but I am not sure and would like to know if there is some way I can make sure my Ubuntu doesn't have error or anything, thanks.

What did you delete?

---

### Post by TheNerdAL on 2010-04-15
I have no idea, I ran Computer Janitor and deleted stuff that I didn't use and I read somewhere that it can be bad to use that.

---

### Post by TheNerdAL on 2010-04-15
But I also heard that fsck, which scans for errors, scans automatically every something amount of boots, right? Does it automatically scan and FIX when my Ubuntu is mounted?

---

### Post by nixclusive on 2010-04-15
fsck is like chkdsk, it will scan and fix filesystem errors only. If you didn't run the said software as a root user or under sudo permissions then you probably don't need to worry about your "system" being in trouble.

---

### Post by TheNerdAL on 2010-04-15
> **nixclusive said:**
> fsck is like chkdsk, it will scan and fix filesystem errors only. If you didn't run the said software as a root user or under sudo permissions then you probably don't need to worry about your "system" being in trouble.

I put my password in before I ran it, does that count?

---

### Post by nixclusive on 2010-04-15
Probably

---

### Post by TheNerdAL on 2010-04-15
My Ubuntu is mounted and I heard it's bad to run fsck. I also heard that fsck runs in X number of boots. Does that apply to me too? And does it fix errors if any?

---

### Post by nixclusive on 2010-04-15
Yes. By default, the system will run fsck on your filesystems periodically (after ever x no. of mounts or after x no. of days, whichever is earlier) or in case of improper shutdown like a power failure. You can force a filesystem check on next boot by issuing the following command: ```
sudo touch /forcefsck
``` Please note that fsck itself cannot detect missing files the operating system may need, it can only ensure that the files already present are in a consistent state.

---

### Post by TheNerdAL on 2010-04-15
> **nixclusive said:**
> Yes. By default, the system will run fsck on your filesystems periodically (after ever x no. of mounts or after x no. of days, whichever is earlier) or in case of improper shutdown like a power failure. You can force a filesystem check on next boot by issuing the following command: ```
sudo touch /forcefsck
``` Please note that fsck itself cannot detect missing files the operating system may need, it can only ensure that the files already present are in a consistent state.

Aww mayne! Lol, thanks anyways. :)

---

