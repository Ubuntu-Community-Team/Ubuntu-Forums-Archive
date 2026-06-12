---
title: "ATTN: Geeks, I need help with a Persistent USB issue"
date: 2010-04-08
forum: General Help
---

### Post by schwabdale on 2010-04-08
I installed 10.04 on a usb stick. Everytime it boots up, I delete the "Install Ubuntu" icon. 
After reboot, its still there. Is there any way to get rid of this icon...besides disabling all
desktop icons through Ubuntu Tweak?

Thanks

---

### Post by ajgreeny on 2010-04-08
Are you sure it's running as a persistent USB and not just as a live CD type USB?

How about saving other configurations and files; does that work?

---

### Post by schwabdale on 2010-04-08
I am running it persistently. Some things are saved. Things like docs, bookmarks, installed software... but things like passwords, install Ubuntu on the desktop,... keeps going back to default. 

What do think? Is there any way to get rid of this icon?

---

### Post by schwabdale on 2010-04-09
Maybe this is not possible because it is essentially a live cd with an area on it to save data

---

### Post by codemaniac on 2010-04-09
would you please clarify how did you install it in your flash drive, i mean if by the means of "liveusbcreator"(persistent) or Unetbootin or ubuntu installer>>>>???

---

### Post by schwabdale on 2010-04-09
I have tried all of these options. This install was from the cd. I just clicked on Startup disk creator.

---

### Post by Monotoko on 2010-04-09
You could try this to get the full environment:

Put the live CD disk into the computer, plug your USB drive in, then instead of installing to your harddrive, install to the USB drive (you will have to click to get advance partitioning, and remember to turn SWAP off)

This will give you a USB stick with GRUB and Ubuntu on it :)

---

### Post by schwabdale on 2010-04-09
I tried that before, but it just booted with a blinking cursor. Although I didn't turn swap off! Maybe that would work. 

If I installed it this way, would this give me the availability to move it from one computer to the other with no problems? Would it see other computers windows installations?

---

### Post by Directive 4 on 2010-04-09
> **schwabdale said:**
> I tried that before, but it just booted with a blinking cursor. Although I didn't turn swap off! Maybe that would work. 

If I installed it this way, would this give me the availability to move it from one computer to the other with no problems? Would it see other computers windows installations?

this way is good, you need to remember to install the bootloader on the usb,

any computers hdd's will be mountable, and data can be retrived from them.

---

### Post by schwabdale on 2010-04-09
How do you install the boot loader to the usb?

---

### Post by Directive 4 on 2010-04-09
yea, just from live cd go throu full install to usb, some option will be advanced, click here, 

then choose where to install the bootloader, 

right up to you lick install you can go back to begaining of process, so have a good look around.

---

### Post by schwabdale on 2010-04-09
Thanks for all the help!

---

