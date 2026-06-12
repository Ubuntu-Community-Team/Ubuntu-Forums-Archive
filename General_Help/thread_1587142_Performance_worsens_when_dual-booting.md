---
title: "Performance worsens when dual-booting"
date: 2010-10-03
forum: General Help
---

### Post by bonixavier on 2010-10-03
Hello forum!

I've been experiencing a strange thing regarding my Lucid's performance. I used to have it as the single OS installed, but I had to install Winblows because I was unable to get Civilization V running with Wine (I've seen that some people could, I couldn't). Now I've noticed a big drop in performance in my PC.

Booting is about as fast as ever, but, for some reason, programs take longer to load and I've been hearing the processor doing its job (you know that annoying little sound)? Is this a known issue with dual-boot or it may be some hardware failing?

Other than that, is there anything you can recommend to boost Ubuntu's performance? It got me hooked on Linux and I don't think there's a going back for me - I now feel Windows treats you like a retard most of the time, prevents you from accessing the system core and, when you finally get into trouble, it turns into a cryptic system only intelligible to initiates.

Sorry for the wall of text folks. Thanks in advance. :D

---

### Post by DeMus on 2010-10-03
How did you install Windows? Did you choose an empty part of the hard-disk, installed it and re-organized Grub to have Windows included in your boot choices?
If so, then having another OS (even Microsoft's OS) does not interfere with your Ubuntu installation. That's why you have Grub: you choose one OS and the other is completely dead at that time. It's on disk but that's it, it doesn't work at all.

Didn't you do something else around the same time which might have slowed down Ubuntu?
Open a terminal en type top. Look at the top of the list to see which program uses the CPU most and how much it uses.

---

### Post by Mark Phelps on 2010-10-03
I've been multi-booting MS Windows versions with Ubuntu versions since the 7.04 days and I have yet to see any performance drop in Ubuntu in multi-boot install mode.

I have not tried the Wubi option -- MS Windows is fickle enough as is with MS products.  Don't need to have an MS Windows crash take Ubuntu down with it.

---

### Post by bonixavier on 2010-10-05
So, thanks for your help. I later saw that my /home partition file system was not clean. I assume that's what was causing the bad performance? I cleaned it with fsck and it began working normally again. Now I have another problem that I'll post in another thread.

---

