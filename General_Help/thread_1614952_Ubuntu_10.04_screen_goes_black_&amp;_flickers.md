---
title: "Ubuntu 10.04 screen goes black &amp; flickers"
date: 2010-11-06
forum: General Help
---

### Post by hawkalan on 2010-11-06
I recently installed 10.04 and while it works for a while, suddenly the screen will turn black and I guess it locks up.  The disconnect message from the display will occasionally flash on.  Here are my devices:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:0a.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


This obviously is very annoying.  Any help would be appreciated.

Thanks

---

### Post by sikander3786 on 2010-11-06
Hi and Welcome to the forums :popcorn:

Hold down the shift key at your computer's bios screen. It will bring up the Grub menu. Highlighting the first entry, press 'e' to edit it. Navigate to the words "quiet & splash", delete them and type "i915.modeset=1" in their place. Press Ctrl + X to continue booting and try to do regular activities on your desktop and see if the crash/black screen problem occurs again.

If it doesn't you can later make those changes permanent. But first give it a try.

There might be some other causes as well but the above mentioned is a solution to the one that I have encountered the most so we will get to the other one's once this is ruled out.

---

### Post by hawkalan on 2010-11-06
I made the change and so far so go.  Thank you very muh!

---

### Post by sikander3786 on 2010-11-06
> **hawkalan said:**
> I made the change and so far so go.  Thank you very muh!
Glad to hear it is working. Just keep on testing it and when you are satisfied, you'll need to make those changes permanent in /etc/default/grub. But we would like to know first if it actually worked.

Waiting...

---

### Post by Rubi1200 on 2010-11-06
After following sikander's advice, you can make the changes more permanent using the workarounds mentioned here (you need to use the one specific to your card; Workaround G):
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

(on a side note: adding the parameter to /etc/default/grub is only a temporary solution: the real problem is with the way the Intel chipset works with the 10.04 kernel)

---

### Post by hawkalan on 2010-11-06
I spoke too soon.  It had been working all day, then it did it again.  What do you suggest I do next?

thanks

---

### Post by sikander3786 on 2010-11-06
Did you follow the link provided by Rubi1200 in his above post?

---

### Post by hawkalan on 2010-11-06
No. should I do that?

---

### Post by sikander3786 on 2010-11-06
> **hawkalan said:**
> No. should I do that?
Yes that is what it is intended for. Workaround G on that page.

---

### Post by hawkalan on 2010-11-06
[COLOR=Yellow][COLOR=Red]In A) do I do?:[/COLOR]
[/COLOR]
For release we made the decision to blacklist KMS for  8xx hardware. If you had found that beta1 and earlier Ubuntu had been  working fine, this may be an effective workaround for you. 
To turn KMS back on, run this command in a Terminal window and reboot: 
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -uIn  some cases, this bug causes i8xx users to boot into a blank screen on  both the LiveCD/USB and a clean install or upgrade. To enable the above  workaround in these situations, add "i915.modeset=1" to your kernel boot  parameters. 

[COLOR=Red]AND ?:[/COLOR]
**From an installation:**

 1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash".   [COLOR=Red]I removed "quiet splash" was this incorrect??[/COLOR]
4) Ctrl+x to boot. 

[COLOR=Red]
DO I DO THIS also?   Not sure what this means?? I AM CONFUSED>>>>>>>[/COLOR]

If adding "i915.modeset=1" to your boot parameters allows you to boot  successfully, you then need to enter the command above into a terminal  to make the changes permanent.

---

### Post by P4man on 2010-11-06
If you add the parameter in grub (after pressing shift), it only applies for a single boot. Each time you reboot youd have to it again. Its only useful to test.

Since the workaround seems to work, make it permanent by editing /etc/default/grub as explained in the above link (I assume) or the on in my sig.

---

### Post by sikander3786 on 2010-11-07
> **hawkalan said:**
> [COLOR=Yellow][COLOR=Red]In A) do I do?:[/COLOR]
[/COLOR]
For release we made the decision to blacklist KMS for  8xx hardware. If you had found that beta1 and earlier Ubuntu had been  working fine, this may be an effective workaround for you. 
To turn KMS back on, run this command in a Terminal window and reboot: 
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -uIn  some cases, this bug causes i8xx users to boot into a blank screen on  both the LiveCD/USB and a clean install or upgrade. To enable the above  workaround in these situations, add "i915.modeset=1" to your kernel boot  parameters. 

[COLOR=Red]AND ?:[/COLOR]
**From an installation:**

 1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash".   [COLOR=Red]I removed "quiet splash" was this incorrect??[/COLOR]
4) Ctrl+x to boot. 

[COLOR=Red]
DO I DO THIS also?   Not sure what this means?? I AM CONFUSED>>>>>>>[/COLOR]

If adding "i915.modeset=1" to your boot parameters allows you to boot  successfully, you then need to enter the command above into a terminal  to make the changes permanent.
First of all type these 2 commands, one by one in a terminal

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
```

```
sudo update-initramfs -u
```

After completed these 2, reboot. If you get to the desktop you don't need to do anything. If you only get a blank screen, you need to follow this.

> In some cases, this bug causes i8xx users to boot into a blank screen on both the LiveCD/USB and a clean install or upgrade. To enable the above workaround in these situations, add "i915.modeset=1" to your kernel boot parameters. 

Press 'e' to edit the kernel boot line and add "i915.modeset=1" after "quiet & splash" or in place of "quiet & splash". Doesn't matter if you remove "quiet & splash". Quiet & splash makes you boot Ubuntu by showing a splash screen and hiding all the text messages during the boot.

Now for workaround E. edit /etc/X11/xorg.conf by

```
gksudo gedit /etc/X11/xorg.conf
```

and paste these lines at the end of the file.

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "DRI" "off"
EndSection
```

Save and close xorg.conf.

Reboot and hope it all goes well.

---

### Post by hawkalan on 2010-11-07
I do not have a xorg.conf file  only xorg.conf.failsafe.

---

### Post by sikander3786 on 2010-11-07
> **hawkalan said:**
> I do not have a xorg.conf file  only xorg.conf.failsafe.
There should be one even if it is empty. Are you sure you typed a capital X for X11?

Ok try to backup the existing one by

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

And now try to generate a new one by

```
sudo dpkg-reconfigure xserver-xorg
```

See if it generate and put those lines in there.

---

### Post by hawkalan on 2010-11-08
after doing the commands you suggested here is what I got:

desktop:/etc/X11$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
cp: cannot stat `/etc/X11/xorg.conf': No such file or directory
desktop:/etc/X11$ sudo dpkg-reconfigure xserver-xorg
desktop:/etc/X11$ ls -l
total 76
drwxr-xr-x 2 root root  4096 2010-08-16 04:50 app-defaults
drwxr-xr-x 2 root root  4096 2010-08-16 04:50 cursors
-rw-r--r-- 1 root root    14 2010-08-16 04:51 default-display-manager
drwxr-xr-x 6 root root  4096 2010-08-16 04:46 fonts
-rw-r--r-- 1 root root 17394 2009-12-03 04:56 rgb.txt
lrwxrwxrwx 1 root root    13 2010-10-30 00:04 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2010-08-16 04:50 xinit
drwxr-xr-x 2 root root  4096 2010-04-15 07:12 xkb
-rw-r--r-- 1 root root   269 2010-11-03 22:30 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 2010-04-01 06:19 Xreset
drwxr-xr-x 2 root root  4096 2010-08-16 04:38 Xreset.d
drwxr-xr-x 2 root root  4096 2010-08-16 04:38 Xresources
-rwxr-xr-x 1 root root  3730 2010-04-01 06:07 Xsession
drwxr-xr-x 2 root root  4096 2010-10-30 08:29 Xsession.d
-rw-r--r-- 1 root root   265 2008-07-01 12:41 Xsession.options
-rw------- 1 root root   601 2010-08-16 04:38 Xwrapper.config


What do you think is going on here?

Thanks

---

### Post by hawkalan on 2010-11-08
still have problems.  Please see previous messages.  Will I always have problems with my current computer.  Is their a version that works with it?

If not what laptop do you recommend  that will not lock up and where some version of Ubuntu works?

Thanks

---

