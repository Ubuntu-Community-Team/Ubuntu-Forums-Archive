---
title: "ram and hard drive"
date: 2010-11-28
forum: General Help
---

### Post by clarodina on 2010-11-28
how much ram including video ram is sufficient to run vbox on ubuntu live cd so that the vdi like xp is smooth sailing?

---

### Post by lobralleo on 2010-11-28
I found that XP runs nicely under VirtualBox with just 256 MB RAM and only 1 MB video memory. If you have something more to spare, you can increase RAM to 512 and video memory to 16 or even to 64 MB.
However, I personally never tried to run VBox from Live CD: I assume that there is no difference, but I can't say it for sure.
I hope this helps you anyway!

---

### Post by clarodina on 2010-11-29
how about vista and win7?

how much ram does ubuntu require to run smoothly?

---

### Post by lobralleo on 2010-11-29
I just realized that you could step into a bigger problem here: since you have to actually install the guest system on a virtual HD, it could be impossible to install it while running a LiveCD, since it would sit entirely in your RAM. If you account for that, I think that you will need at least another GB or two for the XP installation itself.
However, as I said, I never used VBox from the LiveCD, so I might be missing something.

According to Microsoft's specifications, minimum requirements are 512 MB RAM, 32 MB graphics memory and 20 GB hard drive for Vista and 1 GB RAM and 16 GB hard drive for Win7 32bit. If I am correct about the first issue, then it could be impossible to run Vista or Win7 in RAM - unless you have access to a computer with more than 20 GB RAM!

You can find some more numbers here:

[http://windows.microsoft.com/en-us/windows-vista/products/system-requirements](http://windows.microsoft.com/en-us/windows-vista/products/system-requirements)

[http://windows.microsoft.com/en-US/windows7/products/system-requirements](http://windows.microsoft.com/en-US/windows7/products/system-requirements)

If you really want to run these systems as virtual machines, I would suggest to install Ubuntu on a hard drive, and then to install the VMs.

---

