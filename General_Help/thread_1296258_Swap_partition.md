---
title: "Swap partition?"
date: 2009-10-20
forum: General Help
---

### Post by Slug71 on 2009-10-20
I have a test system which im setting up as a multiboot system with a bunch of distros.

Do i need to or should i set up a separate swap partition for each install or will they all look to one swap partition?

Dont wanna waste 16GB if i dont need to.

Sorry if this has been asked before.

---

### Post by Tibuda on 2009-10-20
Yes, you can use the same partition for all distros.

---

### Post by unknownPoster on 2009-10-20
They will all function perfectly well pointing to the same /swap partition. If you know what you are doing, you could point them to the same /home partition, but this can be risky.

---

### Post by NoaHall on 2009-10-20
All Linux systems will share a swap partition(as far as I know, there are none which won't.) You might just need to point to them on install.

---

### Post by Slug71 on 2009-10-20
Wow, that was quick.

Thanks guys.

---

### Post by az on 2009-10-20
Do not suspend (hibernate) your computer since this writes the contents of your ram to the swap space.

I would hot suggest sharing a home partition since the various versions of the software will cause your problems if you share their configuration files.

---

### Post by Slug71 on 2009-10-20
> **az said:**
> Do not suspend (hibernate) your computer since this writes the contents of your ram to the swap space.

I would hot suggest sharing a home partition since the various versions of the software will cause your problems if you share their configuration files.

Yeh i wont be sharing the /home. I foresee way too many headaches.

---

