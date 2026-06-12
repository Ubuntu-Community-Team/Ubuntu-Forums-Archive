---
title: "pciehp problem"
date: 2010-10-16
forum: General Help
---

### Post by Random_Dude on 2010-10-16
Hi,

I've had this problem back in 9.10 and I was expecting that it would get fixed when I installed 10.10. Turns out it didn't, but it's starting to get really annoying and I can't find a simple solution to the problem.

Every time I boot my laptop (a Packard Bell) I get some error messages similar to these before the splash screen:
```
pciehp 0000:00:1c.5:pcie04: Card not present on Slot(37)
pciehp 0000:00:1c.5:pcie04: Card present on Slot(37)
pciehp 0000:00:1c.5:pcie04: Link Training Error occurs
pciehp 0000:00:1c.5:pcie04: Failed to check link status
```

My computer works fine, but if I have to use Ctrl + Alt + F1, I get the last 2 lines of error messages to appear over and over and over again. I simply can't type anything. :mad:

I found a solution [here]("http://arstechnica.com/phpbb/viewtopic.php?f=16&t=38274") but it involves recompiling the kernel and I don't have that kind of tech knowledge.
Does anyone know how to solve this? At least to stop the error messages from appearing over and over again, I must have the log files full of them and I can't type anything on the command line in case of my computer has a major crash. :(

Thanks.

---

### Post by msandoy on 2010-11-28
Try bumping your thread a few times a week, and also, you should give a bit more information about your HW. There are quite a few Packard Bell laptop's on the market. A description of cpu, chipset, graphics chipset etc, etc, would be nice. At least a full model name for the PB in question.
The thread should probable be in Hardware and Laptops. 
Sorry I can't help you with your problem, but at least I gave you a bump.

---

### Post by Random_Dude on 2010-11-29
> **msandoy said:**
> Try bumping your thread a few times a week, and also, you should give a bit more information about your HW. There are quite a few Packard Bell laptop's on the market. A description of cpu, chipset, graphics chipset etc, etc, would be nice. At least a full model name for the PB in question.
The thread should probable be in Hardware and Laptops. 
Sorry I can't help you with your problem, but at least I gave you a bump.

Thanks for the tip. ;)

It's an EasyNote BG47.
After running lspci I get:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Intel Corporation WiFi Link 5100

```

Is this enough information?

Cheers :cool:

---

### Post by Random_Dude on 2010-12-05
Bump

---

### Post by Random_Dude on 2010-12-12
Bump 2

---

### Post by Random_Dude on 2010-12-21
Bump 3.

---

### Post by Random_Dude on 2010-12-29
Bump 4

---

### Post by Random_Dude on 2011-01-06
Bump 5

---

### Post by Random_Dude on 2011-01-13
Bump 6

---

### Post by Random_Dude on 2011-01-20
Bump 7

---

### Post by Random_Dude on 2011-01-20
Bump 7

---

### Post by Random_Dude on 2011-01-30
Bump 8

---

### Post by Random_Dude on 2011-02-06
Bump 9

---

### Post by Random_Dude on 2011-02-11
Bump 10

---

### Post by Random_Dude on 2011-02-16
Bump 11

---

### Post by Random_Dude on 2011-02-22
Bump 12

---

### Post by Random_Dude on 2011-02-27
Bump 13

---

### Post by Uleti on 2011-03-02
It's easy to make a new kernel recompilation.

I have just the same trouble, and I wrote a tutorial for this.

In spanish, use a translator.

[http://www.linuxmint-hispano.com/foro/??topic=6887.msg42570#msg42570](http://www.linuxmint-hispano.com/foro/??topic=6887.msg42570#msg42570)

HTF

---

### Post by Random_Dude on 2011-03-02
> **Uleti said:**
> It's easy to make a new kernel recompilation.

I have just the same trouble, and I wrote a tutorial for this.

In spanish, use a translator.

[http://www.linuxmint-hispano.com/foro/??topic=6887.msg42570#msg42570](http://www.linuxmint-hispano.com/foro/??topic=6887.msg42570#msg42570)

HTF

Thanks Uleti. ;)
I though nobody would bother to answer by now.

I see that I have no better option than to recompile. I'll try doing this tonight.
BTW, if I use BleachBit, does it erase the huge amount of system logs that I have? Because I've noticed that from time to time I have to use it because my disc space starts to decrease for no apparent reason (must be the logs).

Cheers :cool:

---

### Post by Uleti on 2011-03-02
> **Random_Dude said:**
> Thanks Uleti. ;)
I though nobody would bother to answer by now.

I see that I have no better option than to recompile. I'll try doing this tonight.
BTW, if I use BleachBit, does it erase the huge amount of system logs that I have? Because I've noticed that from time to time I have to use it because my disc space starts to decrease for no apparent reason (must be the logs).

Cheers :cool:


To clean the huge logs you just only erase the files -not directories- in /var/log. That's all

---

### Post by Random_Dude on 2011-03-02
Thanks.

During your tutorial I got an error on step 8:

```
make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
  HOSTCC  scripts/kconfig/lxdialog/inputbox.o
  HOSTCC  scripts/kconfig/lxdialog/menubox.o
  HOSTCC  scripts/kconfig/lxdialog/textbox.o
  HOSTCC  scripts/kconfig/lxdialog/util.o
  HOSTCC  scripts/kconfig/lxdialog/yesno.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
scripts/kconfig/mconf arch/x86/Kconfig
Your display is too small to run Menuconfig!
It must be at least 19 lines by 80 columns.
make[1]: ** [menuconfig] Erro 1
make: ** [menuconfig] Erro 2

```

Do you know what it migth be?

Cheers :cool:

---

### Post by Uleti on 2011-03-02
> **Your display is too small to run Menuconfig**!
It must be at least 19 lines by 80 columns.

Maximize your terminal window. If you use KDE Konsole to use full screen if you use Gnome, gnome terminal also use full screen.

---

### Post by Uleti on 2011-03-03
Hello, I have just compiled the last kernel this mornig. It took two hours and half. 

It has been the socond kernel compilation I have compiled for this annoying trouble of my Packard Bell Easynote laptop.

(First and last Packard Bell I buy).

---

### Post by Random_Dude on 2011-03-03
IT WORKED!!!
I had this problem since Karmic.
Thank you very much Uleti. :D

The tutorial you wrote is great and very simple to follow.
I won't update the kernel anytime soon though, that took me almost 2 hours to compile.

You just helped a lot, thanks. ;)

Cheers :cool:

---

### Post by Uleti on 2011-03-03
My mother tonge is not English -I thing you will have noticed-. It would be great if you wrote this tutorial in a perfect English and put it on a wide known Ubuntu blog.

It has been a pleasure to help you.

Greetings.

---

### Post by Random_Dude on 2011-03-03
Neither is mine.
It just happens that I understand Spanish (but it's also not my mother language). ;)

I could try to roughly translate it and post it here, but I couldn't explain how it works if anyone asked details.

Cheers :cool:

---

### Post by Uleti on 2011-03-03
Remember, delete all *.gz files from your /var/log directory -but don't send it to any trush- and reboot, then have fan with a PC without huge logs.

Cheers from Spain.

---

### Post by Random_Dude on 2011-03-03
Thanks. ;)
It definitely saved me a lot of disk space.

By the way, I've noticed that I installed the kernel version 2.6.35-11 (I think).
This version is a little outdated, the one I had was 2.6.35-27.
Is it possible to get a newer version of the kernel?

I understand that I downloaded the kernel files using this command:
```
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
```

Is there a command for downloading a more recent version?
Should I get the latest stable version form here: [http://www.kernel.org/](http://www.kernel.org/) or should I get the kernel files from Ubuntu?

Cheers :cool:

---

### Post by Uleti on 2011-03-03
No. The  kernel sources you downloaded is 2.6.35-27.48 version. This number -11- it's a revision number... you introduce this number, but I did not understand exactly why... But dont't worry that your new recompiled kernel it's really a 2.6.35-27-48 Ubuntu custom kernel -at this moment, in the future you'll download a newer verion-..

The procedure that you have done it's the right way. Don't worry...



Notice, when a kernel updates be download this new kernel will not be choiced like a default kernel in grub. You'll must to select the new manualy in grub menu, and recompile the kernel source, like today, again.

Don't worry... all it's right now in your system.

---

### Post by Uleti on 2011-03-03
See the real name of the packages generated, and you will be sure which kernel you just has installed. Next update I'll try to fix this, I think this can be made with menuconfig.

---

### Post by Random_Dude on 2011-03-03
Unfortunately I already deleted the generated files (they were too big). So I can't see that. :(

Thank you very much for the help. ;)
 Cheers :cool:

---

### Post by Uleti on 2011-03-03
I found what happens. Next recompilation, we have to fix it when we execute make menuconfig at

General Setup
Arbitrary version signature

This is a security feature... If you don't know what kernel has a remote machine it's more difficult to identify what linux version is running and, therefore, it's more dificult to attack it.

Don't worry, all it's right. Next time you can fix the real version number.

---

### Post by Random_Dude on 2011-03-03
> **Uleti said:**
> I found what happens. Next recompilation, we have to fix it when we execute make menuconfig at

General Setup
Arbitrary version signature

This is a security feature... If you don't know what kernel has a remote machine it's more difficult to identify what linux version is running and, therefore, it's more dificult to attack it.

Don't worry, all it's right. Next time you can fix the real version number.

Thanks. ;)
Interesting security feature though...

If I compile and install a new kernel, does it overwrite this one? Because I can't seem to find it on Synaptic, only the ones I installed normally with the update manager.

---

### Post by Uleti on 2011-03-03
Just look for 2.6.35-11  in Synaptics

---

### Post by Random_Dude on 2011-03-03
Nevermind, I fould it by searching "linux kernel".
It's under the name 2.6.35.11 and not 2.6.35-11.

Once again, thank you for the help, I never though that I would ever get this thing solved. ;)

Cheers :cool:

---

### Post by Uleti on 2011-03-03
I put my laptop to recompile the kernel again just to confirm that setting the correct version number here

General Setup
Arbitrary version signature

in the .config file with manuconfig if really we can obtein the authentic version number.

I'll tell you in a couple of hours.

---

