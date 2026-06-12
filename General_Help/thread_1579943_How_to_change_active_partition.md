---
title: "How to change active partition ?"
date: 2010-09-22
forum: General Help
---

### Post by kikloo on 2010-09-22
Hello,

I am using Ubuntu Live CD. I want to set a partition as active partition in my laptop which is not booting up right now. How can i set a partitoion as active through Ubuntu Live CD ?

Please help.

Thanks.

---

### Post by coffeecat on 2010-09-22
When you say "active", do you mean you want to set the boot flag? You don't need to. Linux doesn't need or use the boot flag. That's for Windows. 

What is the booting problem? It's more likely to be a grub problem or a misconfigured /etc/fstab. So - boot up with the live CD and run the boot info script from here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post the contents of the RESULTS.txt file and we can see what's wrong. **Please** enclose the text in code tags as described on that link.

**Edit:** or do you mean Windows is not booting on your laptop?

---

