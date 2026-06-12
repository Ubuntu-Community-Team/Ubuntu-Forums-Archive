---
title: "Deleting ubuntu and grub"
date: 2011-01-15
forum: General Help
---

### Post by brodeur235 on 2011-01-15
If i could get a fast reply on this, that would be fantastic...

I listed my laptop on eBay as having windows 7 on it. The computer then sold for a good amount.

Now, I had windows 7 and Ubuntu 10.10 installed on the computer as well as grub. Whenever I booted, grub gave me the option to boot in windows or ubuntu Linux. Now that my computer has sold, as was listed as a single partitioned windows 7 machine, I went into the windows partition and deleted the linux partition, stretching the windows partition over the space where the linux partition used to be. The operation succeeds and all is well.

However, now i turn my computer off and on and grub has gone rougue and its pissing me off a lot. I get this:

Grub rescue> _

How do i get grub to get he heck of the computer? I just want this garbage gone, and a windows 7 single partition.

All help very much appreciated,

Brodeur235

---

### Post by Smart Viking on 2011-01-15
You should boot up with a Windows 7 CD, and reinstall windows 7.

This will also remove GRUB.

---

### Post by brodeur235 on 2011-01-15
If i had a windows 7 cd I would have done that, but unfortunately I don't. It came on the university laptop pre installed.

Brodeur235

---

### Post by PRC09 on 2011-01-15
As long as you have a dvd drive.....



[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Quackers on 2011-01-15
No need to re-install.
Enter the recovery console of the repair cd and in the command prompt enter ```
bootrec.exe /fixmbr
```
That should get Windows booting again, assuming that the boot flag is set on the Windows partition!

---

### Post by brodeur235 on 2011-01-15
PRC09 and Quackers. You guys are fantastic, I appreciate the help so much, I will get my $700.00 after all, despite all this trouble I brought on myself. Thanks again,

Brodeur235

---

