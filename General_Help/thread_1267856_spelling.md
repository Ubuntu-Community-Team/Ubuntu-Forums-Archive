---
title: "spelling"
date: 2009-09-16
forum: General Help
---

### Post by mike67114 on 2009-09-16
I feel like I'm a candidate for "Dumb and Dumber". 

I misspelled my computer name. How can I fix this?

Thanks!

---

### Post by wilee-nilee on 2009-09-16
A quick web search brought me to this link, several other links gave the same instructions, personally I have never tried this.
 
[http://ubuntuforums.org/showthread.php?t=688018](http://ubuntuforums.org/showthread.php?t=688018)

---

### Post by The Cog on 2009-09-16
> **mike67114 said:**
> I misspelled my computer name. How can I fix this?

You need to change it in both /etc/hostname and /etc/hosts. Open both files for editing before saving either - sometimes changing only one breaks sudo so that you can't then start editing the other.

Then reboot.

---

