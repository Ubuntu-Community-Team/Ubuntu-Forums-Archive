---
title: "See grub prompt and cannot boot ubuntu (wubi)"
date: 2010-02-14
forum: General Help
---

### Post by derkrampus on 2010-02-14
I installed some Ubuntu updates, not sure which, and now I can't boot into Ubuntu (Wubi).  I see the Windows boot manager selection menu, and then I see the Grub prompt (GNU GRUB version 1.97~beta4 - sh:grub>).  This is the 3rd time I've gotten this problem!  I uninstalled Wubi and then reinstalled the past couple times.  I don't want to again!

1) How can I recover my Ubuntu?  

I'm looking at this document, [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode).  I was able to find my boot directory (ls (loop0)/boot.  Now what do I do?

I do see files like vmlinuz-numbers-generic and initrd.img-version-generic.  I do have a grub.cfg file in the /boot/grub directory.  I don't see any .MOD files.  

2) How do I prevent this from happening?

Thanks!
L

___________________
The Identity Access Management Kerfluffle
[http://sites.google.com/site/identityaccessmngmt/](http://sites.google.com/site/identityaccessmngmt/)

---

### Post by Eredeath on 2010-02-14
Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+s...9/comments/210](https://bugs.launchpad.net/ubuntu/+s...9/comments/210)

---

### Post by Ricket on 2010-02-15
> **Eredeath said:**
> Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+s...9/comments/210](https://bugs.launchpad.net/ubuntu/+s...9/comments/210)

I'm having the same problem. You excited me for a second! But you put a literal "..." in your URL, so it's broken. Can you fix it please?

---

### Post by Eredeath on 2010-02-15
> **Ricket said:**
> I'm having the same problem. You excited me for a second! But you put a literal "..." in your URL, so it's broken. Can you fix it please?
I'm sorry.
Here:
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by derkrampus on 2010-02-16
Thanks it worked!  Is there anything I can do to prevent this in the future?
\\:D/

---

### Post by Eredeath on 2010-02-16
> **derkrampus said:**
> Thanks it worked!  Is there anything I can do to prevent this in the future?
\\:D/

To prevent it with Wubi, don't install Kernel or Grub updates. I didn't want to do this (i had the same problem you had) so personally, I copied the entire operating system except for mounted media, /host and /boot and i think /proc into a tar file that i stored on windows. Then partitioned my hard drive, Downloaded and burned Ubuntu to a CD then installed it on that partition. Then I pasted OS i had under Wubi onto that partition.

---

### Post by meierfra. on 2010-02-16
>  Is there anything I can do to prevent this in the future?
Replacing the  wubildr is a permanent fix. It won't happen again.

---

### Post by jerobillard8 on 2010-03-06
Wow this worked I have read a lot of threads on how to fix this. This is the easiest working solution I have found. Great Job! Thank you! Thank You! Thank You!

---

