---
title: "Can't boot Ubuntu via USB"
date: 2012-04-29
forum: General Help
---

### Post by Zeven on 2012-04-29
I have been trying to boot Ubuntu, Xubuntu, Mint LXDE, openSUSE, Fedora, and so on, via USB on my recently built machine using the [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") (the most recent version) which has never let me down in the past. I tell my computer to boot from the USB, it does, the Ubuntu/Xubuntu/Mint LXDE/other options come up, I choose the one that allows me to simply try them, stuff starts loading that a newbie like me cannot decipher, and then a blank screen. I left my desktop running for several minutes each time, but nothing. Strangely enough, when using the exact same method with Puppy Linux, it works fine. They also boot up fine on my HP Pavilion dv6000 laptop that is older than three years.

My specs are:

   [LIST]
[*]Intel Core i5 2500K
[*]    Gigabyte GA-Z68AP-D3
[*]    8Gb (2x4Gb) Corsair Vengeance @ 1600Mhz
[*]    1TB Seagate Barracuda 7200RPM
[*]    Gainward GeForce GTX 570 Golden Sample
[*]    Antec TruePower New Modular 650W
[*]    Lian-Li PC-K63B First Knight
[*]    Windows 7 Home Premium 64bit
[/LIST]

---

### Post by gordintoronto on 2012-04-29
Nice machine!

Right after you turn on the computer, hold down the shift key. When the configuration screen comes up, press F6 and add some combination of these parameters:

acpi=off noapic nolapic nomodeset

The most important one is probably nomodeset. For more information:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Zeven on 2012-04-29
> **gordintoronto said:**
> Nice machine!

Right after you turn on the computer, hold down the shift key. When the configuration screen comes up, press F6 and add some combination of these parameters:

acpi=off noapic nolapic nomodeset

The most important one is probably nomodeset. For more information:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thank you!

Don't know what the shift key is for but on my computer it's F12 to open the boot menu and select a USB device from there. I tried this with openSUSE since it was already on the USB stick (one had to click F4 in this case) and tried all of the options but none of them booted up openSUSE on my desktop. There were only four options to boot, namely "No ACPI," "No Local ACPI," "Default," and "Safe Settings" or something along those lines.

I then tried Ubuntu and the configuration screen looked nothing like it did in your link. Couldn't find those options unter F6 either. See:

[IMG]http://img94.imageshack.us/img94/9977/20120429231000.jpg[/IMG]

---

### Post by Zeven on 2012-04-30
Anybody? I would really like to use Linux on my far more powerful and newer desktop and not just on my over three year old laptop. :(

---

### Post by gordintoronto on 2012-04-30
When you reach the screen pictured in your message, press F6. I think you can type a space and the word "nomodeset" and press enter. No guarantee, but it might work.

As you say, they have changed the appearance during booting quite a lot.

By the way, "can't boot via USB" isn't your problem. It's what happens after booting that is at issue.

---

### Post by sudodus on 2012-04-30
> **Zeven said:**
> Anybody? I would really like to use Linux on my far more powerful and newer desktop and not just on my over three year old laptop. :(
I would suggest the same thing as *gordintoronto*. Try one or several of the boot options and repeat the procedure, because there are many combinations. And read the help text in the link below about boot options!
> **gordintoronto said:**
> Nice machine!Nice machine!

Right after you turn on the computer, hold down the shift key. When the configuration screen comes up, press F6 and add some combination of these parameters:

Right after you turn on the computer, hold down the shift key. When the configuration screen comes up, press F6 and add some combination of these parameters:

acpi=off noapic nolapic nomodeset

The most important one is probably nomodeset. For more information:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Zeven on 2012-04-30
F6 does nothing but make my desktop beep when I press it. No popup menu, no activation of the inline editing of the boot command. Pressing Esc gives me "Boot:" where I then type in "nomodeset" which in return tells me "No kernel image was found" or something along those lines. I am a sad panda.

---

### Post by oldfred on 2012-04-30
Are you perhaps in UEFI mode? 

Most i5 systems have motherboards that use UEFI, but boot in BIOS mode also.

---

### Post by Zeven on 2012-04-30
> **oldfred said:**
> Are you perhaps in UEFI mode? 

Most i5 systems have motherboards that use UEFI, but boot in BIOS mode also.

UEFI mode? Sorry, but how do I check?

---

### Post by oldfred on 2012-04-30
You proably are in BIOS mode. Your system seems to auto check if gpt and then use efi.

> EFI CD/DVD Boot Option
Set this item to EFI if you want to install the operating system to a hard drive larger than 2.2 TB. Make sure
the operating system to be installed supports booting from a GPT partition, such as Windows 7 64-bit and
Windows Server 2003 64-bit. Auto lets the BIOS automatically configure this setting depending on the
hard drive you install. (Default: Auto)


It also sets legacy IDE as default. Most new SATA drives work better with AHCI, but with Windows you have to install drivers first before changing and AHCI does not work so well with XP.

---

### Post by mendhak on 2012-04-30
I believe you need to wait for this screen:

[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png?cache=[/IMG]

When you see that icon, press any key, and you will get this screen:

[img]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=Boot-Options.png[/img]

See the options at the bottom, if you press F6 you then get a popup menu where you can choose acpi/no acpi.  

I have a similar setup as yours and I could only run the Live USB after using noapic and noacpi.  Note that the installer may appear with 'low grade' graphics and a small resolution and that's normal.  Once you install the OS everything should be OK.

---

### Post by Zeven on 2012-04-30
> **oldfred said:**
> You proably are in BIOS mode. Your system seems to auto check if gpt and then use efi.

It also sets legacy IDE as default. Most new SATA drives work better with AHCI, but with Windows you have to install drivers first before changing and AHCI does not work so well with XP.

Set that option to EFI, NON-EFI, and back to Auto and it still won't boot up. Couldn't find anything regarding IDE or AHCI.

---

### Post by Zeven on 2012-04-30
> **mendhak said:**
> I believe you need to wait for this screen:

[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png?cache=[/IMG]

When you see that icon, press any key, and you will get this screen:

[img]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=Boot-Options.png[/img]

See the options at the bottom, if you press F6 you then get a popup menu where you can choose acpi/no acpi.  

I have a similar setup as yours and I could only run the Live USB after using noapic and noacpi.  Note that the installer may appear with 'low grade' graphics and a small resolution and that's normal.  Once you install the OS everything should be OK.

I managed to get to that screen by using [LinuxLive USB Creator]("http://www.linuxliveusb.com/") and then played around with all the options under F6, selecting all and then deselecting one from the bottom every time. No luck, though. I might try it again as it is the closest I have gotten to success but it shouldn't be this time consuming. THe distros work fine on my much older, less powerful laptop.

---

### Post by Zeven on 2012-05-01
I assume this problem isn't HDD related so even if I buy a new HDD dedicated to Linux like I originally intended to, this won't solve my issue.

---

### Post by sudodus on 2012-05-02
I suggest that you keep testing various combinations of boot options with Ubuntu.

But at some point, I think you need to try something else. One option is to try another linux distribution. ***Knoppix*** is known to be very good at recognizing and cooperating with different hardware. So you might download the iso file and try it.

Knoppix used to be 'only live', but the new version can also be installed. It is based on Debian and uses LXDE.

---

### Post by Zeven on 2012-05-03
> **sudodus said:**
> I suggest that you keep testing various combinations of boot options with Ubuntu.

But at some point, I think you need to try something else. One option is to try another linux distribution. ***Knoppix*** is known to be very good at recognizing and cooperating with different hardware. So you might download the iso file and try it.

Knoppix used to be 'only live', but the new version can also be installed. It is based on Debian and uses LXDE.

I would need to get back that other live USB creator to do that. Why would I get different results with different live USB creators, though?

Torrented the iso file, put it on a USB, booted from USB, Knoppix was loading up, all looked well, then a blank screen, just like with all the other distros. You are right, this isn't a boot problem, it just stops showing an image on my screen while loading, or in the case of openSUSE, just continues to show the same thing.

On a somewhat unrelated note, I am not particularly a fan of LXDE and XFCE (at least for my desktop) considering that it's a pretty good machine and can easily handle Unity, KDE, and GNOME. Anything to at least be able to properly boot into a distro, though!

---

### Post by oldfred on 2012-05-03
Almost all the smaller distributions use a default video mode that just works with just about anything.
With your nVidia and Ubuntu you usually need nomodeset on liveCD and on the first boot after install or until nVidia driver is installed.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sudodus on 2012-05-03
> **Zeven said:**
> I would need to get back that other live USB creator to do that. Why would I get different results with different live USB creators, though?

Torrented the iso file, put it on a USB, booted from USB, Knoppix was loading up, all looked well, then a blank screen, just like with all the other distros. You are right, this isn't a boot problem, it just stops showing an image on my screen while loading, or in the case of openSUSE, just continues to show the same thing.

On a somewhat unrelated note, I am not particularly a fan of LXDE and XFCE (at least for my desktop) considering that it's a pretty good machine and can easily handle Unity, KDE, and GNOME. Anything to at least be able to properly boot into a distro, though!
I really hope your case will not be typical for new hardware, but instead I hope that there will soon be a built-in driver in Ubuntu that can manage new graphic cards.

An alternative today is to use the alternate download iso file
[[COLOR="Red"]_http://www.ubuntu.com/download/desktop/alternative-downloads_[/COLOR]]("http://www.ubuntu.com/download/desktop/alternative-downloads")
and after installation of Ubuntu boot into recovery mode (the second option in the grub menu after installation) to download and install the graphics driver, and finally after that to run in graphics mode.

---

### Post by Zeven on 2012-05-03
> **oldfred said:**
> Almost all the smaller distributions use a default video mode that just works with just about anything.
With your nVidia and Ubuntu you usually need nomodeset on liveCD and on the first boot after install or until nVidia driver is installed.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I managed to boot into Ubuntu 12.04! I created a live USB with Ubuntu on it, booted it up, went to help, typed in menu, that brought me back to the menu (the way it's supposed to look like this time), pressed F6, selected nomodeset, and it fully loaded up. The resolution was pretty low and it had a 4:3 aspect ratio but hey, it's an improvement. I couldn't change the resolution or the aspect ratio and it said "Laptop" in the display settings despite me being on a desktop as well. What's more, openSUSE didn't have the nomodeset option, and I doubt Fedora and the other Linux distros not related to Ubuntu will either.

---

### Post by sudodus on 2012-05-03
> **Zeven said:**
> I managed to boot into Ubuntu 12.04! I created a live USB with Ubuntu on it, booted it up, went to help, typed in menu, that brought me back to the menu (the way it's supposed to look like this time), pressed F6, selected nomodeset, and it fully loaded up. The resolution was pretty low and it had a 4:3 aspect ratio but hey, it's an improvement. I couldn't change the resolution or the aspect ratio and it said "Laptop" in the display settings despite me being on a desktop as well. What's more, openSUSE didn't have the nomodeset option, and I doubt Fedora and the other Linux distros not related to Ubuntu will either.
Congratulations :KS

Now I suggest that you accept the offer, that I think should appear, to select a proprietary driver for your nvidia card. Otherwise, search for that option in the menu system or try 
```
jockey-gtk
```. If that doesn't help either, try to download and install nvidia's own driver (but that would be the last option, because it is a little tricky).

---

### Post by Zeven on 2012-05-06
> **sudodus said:**
> Congratulations :KS

Now I suggest that you accept the offer, that I think should appear, to select a proprietary driver for your nvidia card. Otherwise, search for that option in the menu system or try 
```
jockey-gtk
```. If that doesn't help either, try to download and install nvidia's own driver (but that would be the last option, because it is a little tricky).

THank you! No such offer appears, unfortunately.This is what I get after I put in the command you suggested:

[IMG]http://img851.imageshack.us/img851/3200/screenshotfrom201205061v.png[/IMG]

So I found some instructions online after downloading the Nvidia driver and after a while got this:

[IMG]http://img189.imageshack.us/img189/9398/screenshotfrom201205061.png[/IMG]

---

### Post by Zeven on 2012-05-06
Just tried to boot openSUSE, Fedora, and Ubuntu using UNetbootin and the problem persists unforunately. I create these live USBs on my laptop to test on my desktop by the way. Could that be the issue? Should I create them on my desktop instead?

---

### Post by oldfred on 2012-05-06
Are you using the nVidia card or is your motherboard let you use the Intel video mode?  And turn off the nVidia in UEFI/BIOS?

---

### Post by Zeven on 2012-05-06
> **oldfred said:**
> Are you using the nVidia card or is your motherboard let you use the Intel video mode?  And turn off the nVidia in UEFI/BIOS?

The HDMI cable is plugged into my Nvidia card so I assume it's that. How would I go about doing that?

---

### Post by oldfred on 2012-05-06
The z68 boards and Intel chips have built in video from the motherboard. Connectors are with motherboard not video card. 

I think if you also have a video card you turn off the Intel motherboard video in BIOS, but I do not know for sure.

Edit - this may be part of the problem. From Gigabyte

> GIGABYTE Z68 motherboards are enabled with LucidLogix Virtu GPU  Virtualization technology which allows users to dynamically switch  between their built-in graphics and their high-end, 3D discrete graphics  cards.

Switchable graphics have been an issue. I think you have to set one or the other.

---

