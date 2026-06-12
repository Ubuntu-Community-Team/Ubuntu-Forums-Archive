---
title: "ubuntu/xp dual boot help"
date: 2009-09-04
forum: General Help
---

### Post by titanbaseball13 on 2009-09-04
i originally had windows xp installed on my internal hard drive.  i wanted to put ubuntu on it but there wasn't enough space so i installed ubuntu 9.04 on my external hard drive.  now whenever i turn on my computer instead of starting up normally it tries to load grub.  the problem is that it still tries to load grub even when i tell it to boot from the internal hard drive and the external one isn't even plugged in.  since the external one isn't plugged in, grub fails to load and i can't boot into any os.  as of right now i can't boot into anything unless i have my external hard drive plugged in.  what i want to know is if there is a way to have my computer boot into windows xp normally without loading grub unless i tell it to boot from the external hard drive.    any help will be greatly appreciated.

---

### Post by ronparent on 2009-09-04
If you can set the boot order to try to boot first from the external drive, it is a piece of cake. You have to first restore the mbr on the internal drive to boot to windows. You would then have to setup grub to write grub to the mbr of the second drive so that whenever it is plugged in it will control the boot process. Since we are likely shuffling the selected boot drive relative to the install position (not clear from your description) you will probebly have to manually edit /boot/grub/menu.lst to find windows. Voila, mission accomplished. Post here if my impromtu descrition needs some clarification.

Excellent anaysis of your situation by the way.

---

### Post by titanbaseball13 on 2009-09-04
i have a few questions:
1.  to restore the mbr on the internal drive to boot into windows, do i use the windows restore cd and the fixmbr command?
2.  how would i set up grub to write grub to the mbr of the external drive so that it only shows up when i choose to boot from the external drive?
3.  how do i manually edit menu.lst to find windows?
 
if you dont want to spend the time showing me yourself it would be great if you could maybe link me to a website that explains how to do it, maybe one with pictures even.
thanks for your help.

---

### Post by ronparent on 2009-09-05
1. Yes.

2. To setup grub on the mbr of the external drive, boot to the live cd and open a terminal session. In the terminal enter the following commands:

**sudo grub**

and from the grub prompt enter the command:

[B]find /boot/grub/stage1
[/B]
using the location in the output from the above enter:

**root (hdx,y)** - x and y are the numbers in the above output
**setup (hdx)**

**quit** and restart

Everything should now present correctly on boot from the external drive.

3. Booting from the external drive windows will probably be on (hd1). If grub booting from the internal drive found windows on (hd0) that is what would be in your menu.lst. Since windows requires a boot from (hd0) we will additionally need a construct to fool it. To edit menu.lst you need only to boot ubuntu (on the usb) and once ubuntu is up open a terminal session (necessary only to grant yourself permission to edit as admin). To start the edit enter **gksudo gedit /boot/grub/menu.lst**. Navigate to the end of menu.lst where you will find the entries to boot windows - probably in the form rootneverify (hd0,0). Take note of the number after the comma, it may be something other than 0. Simply replace that series of commands with:
[B]
rootnoverify (hd1,x)
map (hd1) (hd0)
map (hd0) (hd1)[/B]
etc.

The map commands are merely necessary to fool window into thinking it is being booted from (hd0). Save and reboot to see if everything works.

That's should be it. Good luck. Post if you run into problems.

---

### Post by titanbaseball13 on 2009-09-05
ok thanks. ill try this out pretty soon and post the results.

---

### Post by jobst on 2009-09-06
> **titanbaseball13 said:**
> i originally had windows xp installed on my internal hard drive.  i wanted to put ubuntu on it but there wasn't enough space so i installed ubuntu 9.04 on my external hard drive.  now whenever i turn on my computer instead of starting up normally it tries to load grub.  the problem is that it still tries to load grub even when i tell it to boot from the internal hard drive and the external one isn't even plugged in.  since the external one isn't plugged in, grub fails to load and i can't boot into any os.  as of right now i can't boot into anything unless i have my external hard drive plugged in.  what i want to know is if there is a way to have my computer boot into windows xp normally without loading grub unless i tell it to boot from the external hard drive.    any help will be greatly appreciated.

thats because the grub wrote itself into the mbr record, don´t do that windows and virus checkers dont like it. however its straight forward to fix it:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

in your case the secondary disk is your usb disk (or whatever).


jobst

---

