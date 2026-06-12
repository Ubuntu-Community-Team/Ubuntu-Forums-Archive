---
title: "External Hard Drive device name"
date: 2010-08-11
forum: General Help
---

### Post by Gurtz on 2010-08-11
Hi all,

I am setting up a Linux laptop for my parents, and want to also create some backup scripts to allow them to easily back up to an external hard drive. [And for them to be able to use it, it has to be super simple.] 

For security purposes (should the external drive ever get lost or stolen), I want to encrypt the entire device using TrueCrypt. That means my scripts will have to use TrueCrypt to mount the backup volume using the device name. [Right?]

Now to the actual question(s):

1) Is there a way to ensure that an external hard drive will ALWAYS be assigned the same device name when plugged in? [That would be the simplest solution for me.]

2) Alternatively, is there a way (using bash scripting) to "find" the device name of a particular external hard drive, even if it might not be known in advance.

Thanks,
Gurtz

---

### Post by dabl on 2010-08-11
> **Gurtz said:**
> Hi all,

1) Is there a way to ensure that an external hard drive will ALWAYS be assigned the same device name when plugged in? [That would be the simplest solution for me.]



Not by /dev/sd_x_ number.  But:

- the partition (which is what you actually mount) will always be the same UUID number (hint -- you can use mount "by-uuid")

- if you give the partition a LABEL, then it will always be the same (hint -- you can use mount "by-label")

---

### Post by Gurtz on 2010-08-11
Awesome! I knew somebody here would have answers for me.

Thanks so much!

Gurtz

---

