---
title: "Can't boot from CD"
date: 2010-06-18
forum: General Help
---

### Post by imjscn on 2010-06-18
I've got serious troulbe at booting. Since I made partition and clean install OS, I can't boot from floppy or CD except Xubuntu Live CD. 

When I insert window xp CD, I can hear it's reading, but just not start. 

When I insert Xubuntu live CD, it takes longer time than usual to start. 

I guess something is damaged at the process of partitioning. Could anybody help?

Thanks!

---

### Post by pricetech on 2010-06-18
Partitioning happens to your Hard Disk Drive, not to your Optical Disk Drive (CDROM, CDRW, DVD, Whatever) so partitioning didn't damage anything.

Are you using the right hotkey to bring up a boot menu so you can choose the boot device ??  Are either the Floppy drive, ODD, or both set to boot before the Hard Drive ??

It has to be something other than the fact that you partitioned you Hard Drive.

---

### Post by ddrichardson on 2010-06-18
Partitioning wont do it. Are the CD's scratch free and is the drive clean (especially if you keep it on the floor).

---

### Post by imjscn on 2010-06-18
Although partition can't damage hardware but it can damage software which control the boot. Maybe the MBR damaged?

I keep thinking why Xubuntu Live CD can still boot while others can't.  This first time I insert the CD was when unable to boot CD  under Windows XP OS.  I choosed "Help me boot from CD", that choice must installed something out of box. Now I formated Winxp and installed Xubuntu(coz later Winxp OS couldn't boot up), that "Help boot from CD" thingy still working out of box helping Xubuntu CD, but not helping others.

Normally when start, there's a Dos line saying "Press any key to boot from CD". Now, there's only a black screen before OS start. I can hear it's reading CD, but can see nothing on screen. I tried to press lots of keys, nothing help.

All the CDs I tried are scratch free and function well in my another computer. The drive is clean.

---

### Post by yetiman64 on 2010-06-19
> **imjscn said:**
> Although partition can't damage hardware but it can damage software which control the boot. Maybe the MBR damaged?

No, when booting from a cd or floppy by BIOS (not software on a drive but from the motherboard), your HDD is not even referred to by BIOS (for the booting), so your problem as reported is very unlikely to be related to your partitioning a HDD.

**Question**: Did your problem with the cd and floppy exist prior to partitioning and re-installing your system, and did you attempt to repair the problem by reinstalling etc.? 
(Just to clarify your situation - for anyone else who can help out.)

Note:>  This first time I insert the CD was when unable to boot CD  under  Windows XP OS.  I choosed "Help me boot from CD", that choice must  installed something out of box. Now I formated Winxp and installed  Xubuntu(coz later Winxp OS couldn't boot up) This to me, would indicate it existed before your repartitioning.

I would also suggest you check inside your computer case for any dust / particle buildup, as this sounds more likely to pertain to the hardware than anything you've currently mentioned (unfortunately it can also indicate a failing motherboard, as both cd and floppy drive is referred to - hope not, for your sake).

---

### Post by imjscn on 2010-06-19
No, CD and Floppy were working perfectly before I run into trouble. Here's how my nightmare started and what I have done:

```
1. Got unwanted winxp sp3 automatic updates, then,  Restored to pervious point via Winxp system restore, then, can't boot  system; can't  boot from Winxp CD either;

2. Boot from Linux Live CD, formate harddisk and install ubuntu;

3. Can boot Linux OS, but black screen at booting. There's no way to see what's going on at booting; Pressing any function key or IBM bottons doesn't return any result, still boot into Ubuntu;

4. Can't boot from any legal bootable CD except Ubuntu Live CD;

5. No way to access Bios to set boot sequence, so, can't boot from USB floppy either;
```

Since the Xubuntu Live CD can still boot, I think a failing motherboard is unlikely. I can hear it's reading the CD, just not boot up. 
It's a laptop, mostly closed cover, very clean.

---

### Post by yetiman64 on 2010-06-19
Ok, that makes the situation clearer (forget the hardware suggestions).

However #5 > No way to access Bios to set boot sequence, so, can't boot from USB floppy either; This is important to access for what you are trying, on most laptops it is either the F2 key or the DELETE key (have you tried these - during the POST boot sequence, but before grub starts loading ?) BTW - POST is the BIOSes "power on self test" sequence.

Now with only 1 linux OS installed grub will not show a bootscreen during the boot, unless you hold down the SHIFT key during its boot (the timing as to when to hold it down is important - ie after the POST screen but before the splash screen shows - hold it down continuously).

As to why the Xubuntu live cd worked, it is most likely that BIOS reverted to the cd drive after you formatted and repartitioned the Win system to Ubuntu and the HDD had no bootable system on it. Hope this helps explain your situation a bit better.

You need to focus on accessing your system BIOS and setting the boot order for what you are doing here, as it is all controlled from the motherboard and NOT the HDD.

---

### Post by wilee-nilee on 2010-06-19
what is your computer model?

---

### Post by imjscn on 2010-06-19
It's Thinkpad T43 2668

Originally can press F8 to access Bios when start, can press F12 to choose booting from other device. Those function keys are not available in a re-installed OS without install IBM's R&R file. So, I'm sure I can't use those keys.
But, before the problem,  if there's CD in the cdrom at start, the starting screen would show "Press any key to boot from CD". Now, there's nothing on the starting screen, all black. I tried my luck pressing any key, doesn't work.

I tried the Shift key to bring starting screen, as mentioned above, it doesn't work either.

---

### Post by wilee-nilee on 2010-06-19
How to access the BIOS - ThinkPad, see if this works it appears that it may not be a f key prompt.
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=YAST-3JWKJX](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=YAST-3JWKJX)

---

### Post by imjscn on 2010-06-19
Thanks. But those function keys were available if I didn't formate the factory original install. After I formated the OS, I need to install their R&R files to active those keys. To install the R&R, I need to install Windows,  still need to boot from CD to be able to install those stuffs.

---

### Post by wilee-nilee on 2010-06-19
I use this technique on a new computer when I'm to lazy to look up the key prompt, hit power then run your finger across all the f keys like you were reading braille going both  directions quickly. From end to end including the esc and del keys. This wont tell you the correct key but will probably get you to the change whats read for boot. 

Your computer will access the bios and your computer will give you the boot from screen if you find the correct keys, call lenovo if you can't figure it out.

---

### Post by imjscn on 2010-06-19
No, they are all inactivated without the R&R files to active them after formated OS.

---

### Post by pricetech on 2010-06-22
The Operating System and the BIOS are two distinctly different things.  You should be able to access you BIOS without an OS even being installed.  The suggestion about swiping the F keys at boot will probably work, if for no other reason than the probability that it will trigger a keyboard error and prompt you with an option to enter the BIOS.

---

### Post by sf-it-services on 2010-06-22
the dragging of the finger along the f-keys...... are you a qualified engineer? perhaps use a pitchfork to take a HDD out too.

DO NOT DO THIS WITH THE F-keys, some machines have system functions installed on f-keys at boot time which could cause problems.

its esc, del, f12, f2....etc, depending on manufacturer it usually shows on the BIOS Splash screen.

---

### Post by pricetech on 2010-06-24
> **sf-it-services said:**
>  perhaps use a pitchfork to take a HDD out too.

NO !!!!!  A cutting torch is the ONLY tool to use for that.

---

