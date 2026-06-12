---
title: "Error: out of disk, grub rescue."
date: 2012-01-25
forum: General Help
---

### Post by AlmostAnnoyed on 2012-01-25
I've just installed Ubuntu 11.10 after wiping Window XP off my lappy. I installed it from a iso burned onto a CD and have just restarted after a successful installation. Now when I boot up I get the error shown in the thread title.

When it comes to problems like this I am a COMPLETE noob so I need the simplest solution possible to tackle this problem.

I've read all sorts of answers and from what I gather it might relate to my hard drive, but like I said I know close to sod all on these things.

Can anyone help?

Thanks :)

Compaq Nc6220
160gb
2.13GHz Pentium M
2GB RAM

---

### Post by drs305 on 2012-01-25
AlmostAnnoyed,

Welcome to the Ubuntu Forums.

This error is sometimes associated with a BIOS limitation which causes Grub to only see the first portion of the hard drive. If you only have one OS, on the first partition, and the files are within the first 137Gb, this shouldn't be a problem.

Rather than worry about the above, the simplest solution for you is probably to boot the LiveCD, install the Boot Repair app, and see if it can fix things.

If it cannot, Boot Repair includes the option to run the boot info script and will provide a link to the contents. If your system is still broken, you can post the link to the RESULTS.txt file and we can take a look at your boot status.

Click the Boot Repair link in my signature line for information on this tool.

---

### Post by AlmostAnnoyed on 2012-01-25
honestly I'm not going to bother with Unbuntu. what a waste of my time.

---

### Post by Apophis93 on 2012-02-23
Drs305,

Thank you for your post, i was having this issue installing on my old Inspiron 9200. USB install would fail loading graphics and software package. Cd install gave me the corrupt grub install but boot-repair fixed that and now I have a working install of Ubuntu studio 11.10 thanks again.

- Daniel

---

### Post by drs305 on 2012-02-23
Apophis93,

Welcome to the Ubuntu forums. 

Glad to see even a thread such as this one can have some redeeming value.

Happy Ubuntu-ing !

---

