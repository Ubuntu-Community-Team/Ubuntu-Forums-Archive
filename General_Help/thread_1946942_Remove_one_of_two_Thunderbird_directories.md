---
title: "Remove one of two Thunderbird directories?"
date: 2012-03-25
forum: General Help
---

### Post by gaines2166 on 2012-03-25
I have two Thunderbird directories:

   ~/.thunderbird/<Profile name>

    ~/.mozilla-thunderbird<Profile name>

Apparently the profile in each (over 700MB) is being kept current.  Do I need both?

I ask because my Simple backup file is about 4GB and I'm running out of room.

10.04

---

### Post by Habitual on 2012-03-25
We'll probably need the Tbird version you are using please. :)

---

### Post by Bobhuber on 2012-03-25
> **gaines2166 said:**
> I have two Thunderbird directories:

   ~/.thunderbird/<Profile name>

    ~/.mozilla-thunderbird<Profile name>

Apparently the profile in each (over 700MB) is being kept current.  Do I need both?

I ask because my Simple backup file is about 4GB and I'm running out of room.

10.04
One  solution. Install FEBE backup utility in TB. Make a backup of your profile then delete both profiles (not the directories)and restore from the backup.It should restore the correct one and tell you which is safe to delete. In 11.10 with TB 11.0 the correct one is .thunderbird.
As usual make sure your system backup is current.
Edit - Looks like TB support only for version 3.1 or less with TEBE as it's called.

---

### Post by Azdour on 2012-03-26
Hi,

Did you miss out a slash in the following path:

> 
~/.mozilla-thunderbird**/**<Profile name>

If so...

On my Ubuntu 10.04 .mozilla-thunderbird is a symbolic link to .thunderbird. so when you go into .mozilla-thunderbird what you really are seeing is the contents of .thunderbird. Thats probably why you see 700Mb reported for each. If this is the case I would not delete either of them.

---

