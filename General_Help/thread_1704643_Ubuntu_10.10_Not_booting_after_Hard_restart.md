---
title: "Ubuntu 10.10 Not booting after Hard restart"
date: 2011-03-10
forum: General Help
---

### Post by lionaneesh on 2011-03-10
Hey Everybody , ):P

When i was working on my ubuntu .. There was a power cut and my UPS also dint supported me..The result was that my system got a hard shutdown..

Now when i fire up my system :-

There is a long error log ending with :-

```

[ 1.906419] [<c0791227>] ? kernel_init+0x0/0x183
[ 1.906419] [<c01040c7>] kernel_thread_helper+0x7/0x10 

```My instincts says that i have corrupted my kerenel_init module..

I just want to know how to fix this...

---

### Post by Rubi1200 on 2011-03-11
Hi,
we need more information about the current state of your setup.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

