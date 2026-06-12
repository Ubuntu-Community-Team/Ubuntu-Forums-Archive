---
title: "How to run memtest86+ from Lucid Lynx CD"
date: 2010-07-20
forum: General Help
---

### Post by osx on 2010-07-20
Anyone know how to run memtest86+ from the Ubuntu 10.04 install CD without having to install Ubuntu? It used to be a menu option at boot, but now you just get the option to install or try Ubuntu. I want to test the RAM on an older system before I install.

Thanks.

---

### Post by hathiphnath on 2010-07-27
I have the exact same question. An excellent feature has either been removed or very throughly hidden!

---

### Post by rubylaser on 2010-07-27
It's not an option on the livecd anymore.  You could either use another Livecd, like GParted, or just make your own Ubuntu Live CD Remix like this...
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

---

### Post by wojox on 2010-07-27
Just boot your computer and hold down the Enter key. Take the Live-CD out.

---

### Post by hathiphnath on 2010-07-27
> **wojox said:**
> Just boot your computer and hold down the Enter key. Take the Live-CD out.
I boot up a PC with Ubuntu 10.04 in the tray
I choose to try Ubuntu, rather than install it
I see the live desktop
I hold down the Enter key
I eject the live CD
No memtest86+ popping up
I close the empty tray
No memtest86+ popping up
I release the Enter key
No memtest86+ popping up

What am I doing wrong?

---

### Post by Bluesan on 2010-07-27
Download and burn a copy from here:

[]("http://download.cnet.com/Memtest86/3000-2086_4-10912366.html")[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

---

### Post by hathiphnath on 2010-07-27
So, the only option is using a dedicated memtest86+ CD or an older Ubuntu distribution which includes it on the disc?

---

### Post by osx on 2010-08-05
> **hathiphnath said:**
> So, the only option is using a dedicated memtest86+ CD or an older Ubuntu distribution which includes it on the disc?

That's a bummer if this is true, but I can't find any way of doing it from the live CD anymore. Holding down the enter key did not work for me either.

Strange that it is an option with an actual install though.

---

### Post by hathiphnath on 2010-08-06
> **osx said:**
> Strange that it is an option with an actual install though.
It is? Where?

---

### Post by osx on 2010-08-06
> **hathiphnath said:**
> It is? Where?

After you install Ubuntu 10.04, it is a boot menu option that appears below the kernel list.

---

### Post by hathiphnath on 2010-08-06
You mean the GRUB menu? I know that pops up in dual boot, but I have never seen it on a pure ubuntu PC.

---

### Post by osx on 2010-08-06
> **hathiphnath said:**
> You mean the GRUB menu? I know that pops up in dual boot, but I have never seen it on a pure ubuntu PC.

Yep, the Grub menu. I have a single boot system with Ubuntu 10.04 and it shows the boot menu.

---

### Post by Tidder on 2010-08-22
> **rubylaser said:**
> It's not an option on the livecd anymore.  You could either use another Livecd, like GParted, or just make your own Ubuntu Live CD Remix like this...
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

Incorrect.

> **hathiphnath said:**
> So, the only option is using a dedicated memtest86+ CD or an older Ubuntu distribution which includes it on the disc?

No, it's still on the live CD.  When booting the CD, you will see a couple of small icons at the bottom of the screen.  One looks like a keyboard, one is a round symbol.  Press the space bar and you'll be presented with the good old language selection and boot menu.  Works fine for me.

---

### Post by Bluesan on 2010-08-25
^,

This proves the point, that you can learn something new every day. Thanks for posting the solution.

---

