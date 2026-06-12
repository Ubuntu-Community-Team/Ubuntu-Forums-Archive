---
title: "Refuses to make my USB bootable"
date: 2009-08-30
forum: General Help
---

### Post by Cruzr on 2009-08-30
I honestly have been trying for months almost to get rid of ubuntu, but seeing as it formatted my windows XP cd for no damn reason I've been mad scrambling to get XP onto a bootable USB drive.

I have the tool to make the USB bootable, and when I go to make it a boot drive with the windows XP ISO, it tells em that it isn't a desktop isntallign ISO, so it can't burn it.

I can't find anythign else that will make USBs bootable, all I find it 500 pages of people asking how to sue syslinux on XP...


Please, for the love of christ, HELP! :(
EDIT: Jaunty ubuntu or whatever, but one day it randomly changed to LXDE out of nowhere, I did NOT install it.

---

### Post by uylug on 2009-08-30
If you're using Ubuntu, you may want to have a look at this tool. It does make bootable usb sticks with linux on them but it may also work for Windows.

If you wanna give it a try, run the following command:

```
sudo apt-get install unetbootin;sudo unetbootin
```

---

### Post by kerry_s on 2009-08-30
i think usb-creator is broken, i been getting that same message.

in the terminal:
**sudo apt-get install --no-install-recommends unetbootin**

after install, it will be under system tools.
select the 2nd option and point it to your iso
make sure it's on the right drive
press ok & let it do its thing.

---

### Post by Cruzr on 2009-08-30
Thank you, both of you.
Trying it now now.
EDIT: It says my list of drives, but they are all /dev/sda or /sdb, ect, how do I know which one is my USB drive?
EDIT2: NVM, I found it, unchecked show all drives and it left two options, the first one was the right one.

---

### Post by uylug on 2009-08-30
Cool! Let us know if you have any problems with it!

---

### Post by Cruzr on 2009-08-30
Ok, it made it bootable, but when I boot from it, i get into a netubootin screen and it has an "automatic boot in 10 seconds" count down, BUT, after the 10 seconds, it just restarts the 10 seconds and repeats forever.

Any help, I couldn't find it on google?

---

### Post by uylug on 2009-08-30
Don't you have like a menu you can choose options from?

---

### Post by Cruzr on 2009-08-30
> **uylug said:**
> Don't you have like a menu you can choose options from?
Press tab to edit options.
-presses tab

Only option it gives me is to change where to boot from.

Exactly what happened the first time I tried.
the path is some ubuntu path I do not know where they are, need me to write them down and type them up here if it helps any?

---

### Post by Cruzr on 2009-08-30
OK, so here is this:

unetbootin
a box
inside the box it says default, black text inside a light brown rectangle

underneath it says press tab to edit options
auto booting in 10(countdown from 10)

I press tab and all of the text under the box turns into
>  /ubnkern initrd=/ubninit _

That's it, that is everything.

---

### Post by Cruzr on 2009-08-30
bump, already third page....

---

### Post by jrox717 on 2009-08-31
I have tried to get unetbootin to do the same thing, with no success. I'm under the impression that the program has to be able to point to the kernel and such, and so only knows how to do that for linux file systems. (or something...)

Question: if you have the Windows ISO, can't you just burn another CD? Or you can look at booting from an ISO on the harddrive. I looked at that a little while ago but never quite figured it out. However, I'm pretty sure it can be done!

---

