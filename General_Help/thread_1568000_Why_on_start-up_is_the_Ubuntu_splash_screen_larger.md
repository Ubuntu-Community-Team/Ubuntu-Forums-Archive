---
title: "Why on start-up is the Ubuntu splash screen larger and lower resolution?"
date: 2010-09-04
forum: General Help
---

### Post by JimBuntu on 2010-09-04
Hello, I've been using Ubuntu for years now and love it. I'm wondering on start-up of my machine, the purple Ubuntu splash screen I see, as well as the blinking cursor before the screen, are now at a lower resolution. They used to come on and be smaller, crisper, and clearer. Now they are larger with less res. Why? What does this mean? All other graphics are perfect.

---

### Post by krishnandu.sarkar on 2010-09-04
That's a common bug after installing NVIDIA / ATI drivers. Follow this to restore Boot Screen : [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by JimBuntu on 2010-09-07
I'll just leave it, if its that hard... That guide doesn't seem very sure about what they are doing... Thanks though.

---

### Post by howefield on 2010-09-07
> **JimBuntu said:**
> I'm wondering on start-up of my machine, the purple Ubuntu splash screen I see, as well as the blinking cursor before the screen, are now at a lower resolution.

Try the sticky in this very forum....

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

A very easy to follow command line method is described.

Although to be honest, it is on my screen for so little time, I don't bother "fixing" it... ymmv.

---

### Post by Ginsu543 on 2010-09-08
Try this simple method:

1) Open Terminal and type:
```

gksu gedit /etc/default/grub

```2) Go to the following line and add the following bolded line:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1920x1200 <-- This sets grub resolution to screen resolution
**GRUB_GFXPAYLOAD_LINUX=1920x1200** <-- This fixes the Plymouth problem you're having

```
3) Reboot and see if your problem is resolved

---

### Post by JimBuntu on 2010-09-08
> **Ginsu543 said:**
> Try this simple method:

1) Open Terminal and type:
```

gksu gedit /etc/default/grub

```2) Go to the following line and add the following bolded line:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1920x1200 <-- This sets grub resolution to screen resolution
**GRUB_GFXPAYLOAD_LINUX=1920x1200** <-- This fixes the Plymouth problem you're having

```
3) Reboot and see if your problem is resolved

Ok, been playin around with it and tried adding my "screen" resolution... to no avail. then went into real GRUB and looked at vbeinfo and the highest resolution i could see was 800x600. Is this as high as i could go cause I typed that in, which was a little better but not even close to what it was? Where did you get the 1920x1200? I guess ill try that... also, you said to add just the bolded line... My grub file does not have the line you have above the bolded. Just the #GRUB_GFXMODE=640x480... So do i add both lines beneath that?

---

### Post by JimBuntu on 2010-09-08
> **Ginsu543 said:**
> Try this simple method:

1) Open Terminal and type:
```

gksu gedit /etc/default/grub

```2) Go to the following line and add the following bolded line:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1920x1200 <-- This sets grub resolution to screen resolution
**GRUB_GFXPAYLOAD_LINUX=1920x1200** <-- This fixes the Plymouth problem you're having

```
3) Reboot and see if your problem is resolved

Confirmed 1920x1200 does not work for me. The best I can do is 800x600x32 direct whatever that means... Why?

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=800x600x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by plucky on 2010-09-08
Run ```
sudo update-grub
``` to make the changes to the grub.cfg file.

All you have done is edit the /etc/default/grub 

To actually make the changes you have to run the "update-grub" command

Good Luck

---

### Post by JimBuntu on 2010-09-08
> **plucky said:**
> Run ```
sudo update-grub
``` to make the changes to the grub.cfg file.

All you have done is edit the /etc/default/grub 

To actually make the changes you have to run the "update-grub" command

Good Luck

Yes, I have done that... Still, just a blinking cursor and a flash of the stock Ubuntu 10.10 screen low res. ```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1680x1050
```

---

