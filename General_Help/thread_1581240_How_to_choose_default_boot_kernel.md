---
title: "How to choose default boot kernel?"
date: 2010-09-24
forum: General Help
---

### Post by aust77 on 2010-09-24
Hello,

   I am currently using Ubuntu Lucid on my desktop (stats are in my signature). I have an older computer, with an Intel i8xx chipset as my graphics card. This has had some instabilities on the previous two Ubuntu releases for me (10.04 and 9.10) which I am hoping will be fixed for Maverick, but thankfully the Ubuntu Wiki managed to provide me with fixes.

   After much tweaking and some luck, I was able to get Ubuntu to work without constantly crashing on kernel versions 2.6.32-21, 2.6.32-22 and 2.6.32-23. Unfortunately, when 2.6.32-24 and 2.6.32-25 came out, I was unable to cease the crashes.
   
   While I am still looking into tweaking the latest kernel version to work perfectly, I would like to know if there was a way for Ubuntu to default boot into a kernel other than the latest. This is because I want to run 2.6.32-23 by default (the latest kernel that I have tweaked properly) until I can configure 2.6.32-24 and 2.6.32-25 as well. I have less computer-savvy family members that use my desktop as well, and it would be a pain for them to have to press shift at every boot and have to select the correct kernel.

Thanks in advance for any help,


aust77

---

### Post by sikander3786 on 2010-09-24
Install startupmanager.

```

sudo apt-get install startupmanager

```

It will show up under System > Administration > Startupmanager. Easy to use.

You can also change that options in the Grub config files but the gui is always easier option.

---

### Post by aust77 on 2010-09-24
Thank you very much sikander! It is appreciated.

Cheers,


aust77

---

