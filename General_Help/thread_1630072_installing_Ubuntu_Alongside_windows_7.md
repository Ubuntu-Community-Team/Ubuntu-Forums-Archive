---
title: "installing Ubuntu Alongside windows 7"
date: 2010-11-24
forum: General Help
---

### Post by yousifmagdi on 2010-11-24
I'm installing Ubuntu on laptop that runs windows 7, and there's only one partition, which have windows7 on it.
I started the setup by booting from USB, and while installing I've checked the Alongside with other OS. but am not familiar with the booting thing, and I want both windows and linux to boot. shall I continue? and what is the (Allocate Drive Space) step is about?

---

### Post by Hippytaff on 2010-11-24
Back up all your important files . The option to install along side other os is to dual boot with windows - see here
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Any problems post back :-)

---

### Post by sikander3786 on 2010-11-24
I would recommend to **Quit** the installer here.

Reboot into Windows 7 and use its partitioning tool to resize your C: partition. Once you've freed up some space, run chkdsk on Windows (some recommend 3 times) and once you are sure everything is working fine, start the Ubuntu installer again.

---

### Post by Hippytaff on 2010-11-24
Sikander is right if you **don't **get the option to install along side the other os, it means that windows is taking up all the space. I thought you were asking if you were choosing the right option to dual boot with windows :-)

---

### Post by warfacegod on 2010-11-24
> **sikander3786 said:**
> I would recommend to **Quit** the installer here.

Reboot into Windows 7 and use its partitioning tool to resize your C: partition. Once you've freed up some space, run chkdsk on Windows (some recommend 3 times) and once you are sure everything is working fine, start the Ubuntu installer again.

+1.

I'd only add that you'll be installing into the space you free up.

---

### Post by CrusaderAD on 2010-11-24
Wubi is cool if you're just messing around.

---

### Post by yousifmagdi on 2010-11-24
will resizing the C partition affect the windows?

---

### Post by sikander3786 on 2010-11-24
> **yousifmagdi said:**
> will resizing the C partition affect the windows?
If you use Windows 7 partitioning tools, it shouldn't at all except that it would obviously shrink the space for Windows.

Resize it and run chkdsk and don't install Ubuntu until you are sure Windows is behaving properly.

Wubi has been mentioned in above post. You can install Ubuntu inside Windows just like you would have installed a program by double clicking a .exe file. But it is a bit problematic, a bit slower and updates break it oftenly.

If you just want to try Ubuntu at the moment, you can go for Wubi. But remember, it is not a long term solution, not intended for production purposes either.

---

### Post by yousifmagdi on 2010-11-24
Thanks guys, that was very helpful. I will continue the installation tomorrow, and I will post if i faced more problems :)

---

