---
title: "Input/Output errors - Linux only | Windows fine"
date: 2011-06-29
forum: General Help
---

### Post by absinthe on 2011-06-29
I'm not even really sure how to explain this but here goes:

Having tried Ubuntu/Arch/Mint, I can install the system, start setting it up, but eventually the system will halt with "Read only" errors, Input/Output errors on the drive the Distro is installed on and crap out.

The crazy thing is, everything is working fine in Windows 7. It is just linux, seemingly. I've checked the hard-drive, memory, etc. I'm at an utter loss as to what is going on!

Help!

---

### Post by cariboo on 2011-06-29
What type of partition are you using EXT3 or EXT4?

---

### Post by absinthe on 2011-06-29
> **cariboo907 said:**
> What type of partition are you using EXT3 or EXT4?

It's EXT4.

---

### Post by psusi on 2011-06-29
When you say you "checked the drive", what do you mean exactly?  It sounds like you have some bad sectors.  Check the output of dmesg for more detailed error messages, and run the long SMART self test with the disk utility.

---

