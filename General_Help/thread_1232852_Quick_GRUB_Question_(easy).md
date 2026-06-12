---
title: "Quick GRUB Question (easy)"
date: 2009-08-06
forum: General Help
---

### Post by nevercroft on 2009-08-06
Can grub be set to load my windows booloader I saw one of my friends laptops booting up and next to his vista install it said (loader)

does this mean it loads the vista bootloader?

If it does, does it do this by default because I need to keep my vista bootloader for reasons that probably can't be mentioned on this forum :-\"

---

### Post by mikewhatever on 2009-08-06
> **nevercroft said:**
> Can grub be set to load my windows booloader I saw one of my friends laptops booting up and next to his vista install it said (loader)

does this mean it loads the vista bootloader?

If it does, does it do this by default because I need to keep my vista bootloader for reasons that probably can't be mentioned on this forum :-\"

Not sure why you think your question is both quick and easy, but the answer is yes. You can install GRUB on an external storage device of some kind or another internal hdd and boot from that.

---

### Post by nevercroft on 2009-08-06
Not sure where you get external storage from. Let me rephrase. 

I am installing ubuntu on my laptop. I have 3 partitions(2 primary 1 logical).

One(primary) is windows. I need to keep its bootloader. 

One partion is for data(primary)

The third partition(logical) is free and I am hoping to install ubuntu on it.

Quick and easy in the sense that it would be easy to keep the windows bootloader when installing ubuntu. Giving me a choice at bootup to boot into windows using its bootloader. Can grub do this?

---

### Post by Stolea on 2009-08-06
AS far as I know, grub does not overwrite the Windows boot loader. Unlike Windoze, which happily overwrites grub. If you install Ubuntu to your computer, grub will list Windows as an available bootable OS. Once you boot up Ubuntu you can change the default OS from Ubuntu to Windows by going System>Administration>Startup Manager. In Boot Options go to Default Operating System and change from Ubuntu to Windows. This will change your default so that you boot into Windoze as normal and Ubuntu by choice.
If Startup manager is not listed you have to go Apllications>Add/Remove and look for Startup Manager and install it.
No problem, gets easy after the 50th time:)

---

### Post by nevercroft on 2009-08-06
awesome dude thanks

---

