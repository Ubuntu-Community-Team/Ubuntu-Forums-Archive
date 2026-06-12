---
title: "Linux on Custom PC?"
date: 2011-11-18
forum: General Help
---

### Post by TehSofaWolf on 2011-11-18
Hiya, I just built a custom PC, and the specs are as follows:

SILVERSTONE 1000W Power Supply
EVGA GeForce GTX 580
Creative PCI Express Sound Blaster X-Fi Titanium
Western Digital VelociRaptor 600GB 10000 RPM 32MB Cache
EVGA X79 SLI Motherboard
12 GB Corsair Memory
Intel Core i7 Sandy Bridge 3.2GHz
--

I'm not really a Linux noob, but I can't figure out why this is happening. I installed ArchLinux successfully to it, but when I tried installing Ubuntu, it wouldn't load, stopping at "spinning up disk..." I then tried Debian, LinuxMint, Fedora, Elementary OS, Lubuntu, all had the same error. It said the device wasn't responding, and that there was an error. :(

Any idea what might be causing this? I did install ArchLinux just fine, I wonder why that one didn't give errors...

The last lines of the dump are:
```

[sdb] Assuming drive cache: write through
[sdb] Attached SCSI disk 

```And after that it does nothing for as long as I wait.

Cheers,
--TehSW

Organization of what works: *LATEST UPDATE*
[QUOTE=The distributions that boot.]
Ubuntu 10.04.3 (x86/64)
Debian 6.0.3 DVD (x86/x64)
ArchLinux (net-install)
Fedora 15 (x86/x64)
[/QUOTE]

[QUOTE=The distributions that don't boot.]
Ubuntu 10.10 (x86/x64) (this surprised me, but it's not the same error as the others, it just generally acts buggy and leaks memory (note that I haven't been able to install it, because of crashing during install))
Ubuntu 11.04 (x86/x64) (alternate installers also won't work)
Ubuntu 11.10 (x86/x64) (alternate installers also won't work)
LinuxMint 12 (x86/64)
LinuxMint Debian (x86/64)
OpenSUSE 12.1  (x86/64)
[/QUOTE]

---

### Post by BillyBoa on 2011-11-18
I think the problem is how you are trying to install the OSs and not the OSs themselves. 

You are making a USB or a Live CD?

And I like your computer!

---

### Post by 4Orbs on 2011-11-18
Did you install Arch from a cd, and if so, will the Arch cd still boot?

---

### Post by TehSofaWolf on 2011-11-18
> **BillyBoa said:**
> I think the problem is how you are trying to install the OSs and not the OSs themselves. 

You are making a USB or a Live CD?

And I like your computer!

Thanks.

I tried both USB and Live CD. Both had the same error. I installed Windows fine on it, so the hardware can work together... :confused:

---

### Post by TehSofaWolf on 2011-11-18
> **4Orbs said:**
> Did you install Arch from a cd, and if so, will the Arch cd still boot?

Yeah, I installed from CD. I don't know if it will still boot, I'm not near it for now, but I'll test in a couple hours.

---

### Post by 4Orbs on 2011-11-18
Sometimes the alternate installer for Ubuntu works when the LiveCD doesn't (in my case)... actually getting it to boot.

---

### Post by TehSofaWolf on 2011-11-18
> **4Orbs said:**
> Sometimes the alternate installer for Ubuntu works when the LiveCD doesn't (in my case)... actually getting it to boot.

Thanks, I'll try that.

---

### Post by BillyBoa on 2011-11-18
Can you use  a Live CD system? Does your computer recognizing the OS?

---

### Post by TehSofaWolf on 2011-11-18
> **BillyBoa said:**
> Can you use  a Live CD system? Does your computer recognizing the OS?

I don't understand the question "Does my computer recognize the OS?". I've never tried using a Live CD on this computer before, as it is new.

---

### Post by David006 on 2011-11-18
The term "using a Live CD" refers to 'WUBI', which is literally running Ubuntu as a Windows application.

The Ubuntu OS is never actually 'installed', but you can see what the PC will look like with Ubuntu on it ..


Also, try from CD or USB after stopping the PC from auto-booting to its choice of media.  Instead, stop it (uually 'F9' for desktop PC), and choose the correct media.

---

### Post by TehSofaWolf on 2011-11-18
> **David006 said:**
> The term "using a Live CD" refers to 'WUBI', which is literally running Ubuntu as a Windows application.

The Ubuntu OS is never actually 'installed', but you can see what the PC will look like with Ubuntu on it ..


Also, try from CD or USB after stopping the PC from auto-booting to its choice of media.  Instead, stop it (uually 'F9' for desktop PC), and choose the correct media.

I'll try WUBI later on thanks. I have been using the Boot Menu to boot the CD's and USB's.

---

### Post by 4Orbs on 2011-11-18
If the Arch cd won't boot anymore, probably nothing else will either. I'm assuming you've checked the md5sums for the different distros, burnt the cd at slowest possible speed and burnt the iso as an image, not data. Odd that the flash drives won't boot.

---

### Post by TehSofaWolf on 2011-11-18
> **4Orbs said:**
> ...probably nothing else will either...
I just don't understand why... I've installed Linux to a few "exotic" things, and I just can't figure out why it won't run on a completely new, normal computer. :(

---

### Post by LinuxFan999 on 2011-11-18
> **David006 said:**
> **The term "using a Live CD" refers to 'WUBI', which is literally running Ubuntu as a Windows application.**

The Ubuntu OS is never actually 'installed', but you can see what the PC will look like with Ubuntu on it ..


Also, try from CD or USB after stopping the PC from auto-booting to its choice of media.  Instead, stop it (uually 'F9' for desktop PC), and choose the correct media.
You are not using WUBI when you use the Live-CD. The CD is independant of Windows, like an Installation of Ubuntu to the hard drive (Without Windows or WUBI). WUBI is only used when you select the "Install inside Windows" Option on the menu that appears after inserting an Ubuntu CD into the DVD drive while running Windows.

---

### Post by 4Orbs on 2011-11-18
What I meant was, if the Arch cd doesn't boot anymore (or Windows cd) then something has happened to your cd drive, maybe it is broken or isn't detected correctly. But if Arch and Windows will still boot, then the burning process used to make the live cd's becomes suspect.

---

### Post by TehSofaWolf on 2011-11-18
> **4Orbs said:**
> What I meant was, if the Arch cd doesn't boot anymore (or Windows cd) then something has happened to your cd drive, maybe it is broken or isn't detected correctly. But if Arch and Windows will still boot, then the burning process used to make the live cd's becomes suspect.

Yeah, but it still doesn't work with USB's, so I think it is something maybe HDD or MoBo related.

---

### Post by davetv on 2011-11-18
> **David006 said:**
> The term "using a Live CD" refers to 'WUBI', which is literally running Ubuntu as a Windows application.

A Live CD boots up a linux kernel/environment from the CD and does not run as a "Windows application".

You have confused WUBI with LiveCD ... entirely different things.

---

### Post by kurt18947 on 2011-11-18
> **LinuxFan999 said:**
> You are not using WUBI when you use the Live-CD. The CD is independant of Windows, like an Installation of Ubuntu to the hard drive (Without Windows or WUBI). WUBI is only used when you select the "Install inside Windows" Option on the menu that appears after inserting an Ubuntu CD into the DVD drive while running Windows.

Good job.  I was hoping someone would catch that.  Just to be clear, when you created the USB, did you use the 'startup disk creator' app from a running Linux install or Unetbootin?  I don't know that just copying an Ubuntu .iso image to a USB drive will boot.  Both 'startup disk creator' and Unetbootin install a boot loader.  Maybe see if your CD or USB drive will boot  another machine if you find one.

---

### Post by 4Orbs on 2011-11-18
It's possible the MoBo boot order was reset. You might go to the BIOS and make sure it's still set to boot cd and usb before hdd.

---

### Post by TehSofaWolf on 2011-11-18
> **davetv said:**
> A Live CD boots up a linux kernel/environment from the CD and does not run as a "Windows application".

You have confused WUBI with LiveCD ... entirely different things.

I was completely thinking this when it was said, but I went along with it anyway, because of the poster's rep.

Alright, I just logged back on my PC, booted up Ubuntu 11.10 x64 USB, and the error is 
```

[sdb] Assuming drive cache: write through
[sdb] Attached SCSI disk

```This occurred 5.0623 seconds into the boot.

I have now waited 5 minutes, and nothing has changed. Could it possibly be due to a HDD driver missing?

---

### Post by 4Orbs on 2011-11-18
```
Alright, I just logged back on my PC, booted up Ubuntu 11.10 x64 USB
```
Maybe I'm misunderstanding your procedure. In order for the live environment to work, you need to reboot your computer while the usb drive is still plugged in... or the live cd is still in the tray.

---

### Post by TehSofaWolf on 2011-11-18
> **4Orbs said:**
> ```
Alright, I just logged back on my PC, booted up Ubuntu 11.10 x64 USB
```Maybe I'm misunderstanding your procedure. In order for the live environment to work, you need to reboot your computer while the usb drive is still plugged in... or the live cd is still in the tray.

Sorry, "logged on" was a poor choice of words. The procedure is as follows...

Turn off computer with USB in.
Turn on.
Hit F9
Boot to USB
Ubuntu Live CD boots.


Edit: I just tried again, and it gave me a new line about 4 seconds later. 
It reads:
```

CE: hpet increased min_delta_ns to 20113 sec

```

---

### Post by 4Orbs on 2011-11-18
And the live media never loads? Sometimes it takes a few minutes before it opens the startup screen. Are you, by chance, using a wifi connection only?

---

### Post by TehSofaWolf on 2011-11-18
> **4Orbs said:**
> And the live media never loads? Sometimes it takes a few minutes before it opens the startup screen. Are you, by chance, using a wifi connection only?

I've been waiting for 20 minutes now, and I'd say its not going to load. I have no WiFi, as well...

---

### Post by David006 on 2011-11-18
> **TehSofaWolf said:**
> I just tried again, and it gave me a new line about 4 seconds later. 
It reads:
```
CE: hpet increased min_delta_ns to 20113 sec

```

This looks a lot like:

Booting in recovery mode stops at "Loading Initial Ramdisk"
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863524)

---

### Post by TehSofaWolf on 2011-11-18
> **David006 said:**
> This looks a lot like:

Booting in recovery mode stops at "Loading Initial Ramdisk"
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863524)

Sorry, I don't know what to do with that information. I looked at the bug report and the code, and it didn't seem similar to my problem.

Edit: I just tried running Fedora 15 x64 from a CD, and it boots up just fine. Ubuntu still not booting.

---

### Post by killermist on 2011-11-18
I don't know if this is related AT ALL, or is something else entirely, but with x64 Linux/BSD, I've seen occasions where all drives will "disappear" on booting x64 because the drives (at the command of the bios) are being held in x32 "compatibility" mode instead of x64 "native" mode or some other such.
It might be worth looking around your bios settings for something that looks like "native" or "64 bit" mode in drive/sata settings.

Again, this may be completely unrelated.  But I remember having a problem like this before, and thought it might help.

---

### Post by TehSofaWolf on 2011-11-19
> **killermist said:**
> I don't know if this is related AT ALL, or is something else entirely, but with x64 Linux/BSD, I've seen occasions where all drives will "disappear" on booting x64 because the drives (at the command of the bios) are being held in x32 "compatibility" mode instead of x64 "native" mode or some other such.
It might be worth looking around your bios settings for something that looks like "native" or "64 bit" mode in drive/sata settings.

Again, this may be completely unrelated.  But I remember having a problem like this before, and thought it might help.

Thanks, I thought I'd played with all the BIOS settings, but I'll give this a try.

---

### Post by TehSofaWolf on 2011-11-19
Aha! After a long night of debugging I finally found out that it was the usb ports and cd drive I was using. Strange that they both wouldn't work, but nonetheless, plugging USB's directly into my MoBo works... I hope. I'm installing Ubuntu 10.04.3 at the moment, I haven't tried Debian or Ubuntu 11.10 yet.

---

### Post by TehSofaWolf on 2011-11-28
...nope. Installing Debian worked great from the back panel, but today I tried installing Ubuntu 11.10 x64, and it had the same error message. Noting that Ubuntu 10.04.3 x64 booted up and installed fine, as did Debian 6.0.3 x64 DVD 01, ArchLinux, and Fedora 15 x64. Ubuntu 11.10 x64 and x32, LinuxMint 12 x64 and x32 (all different DE's tried), LinuxMint Debian, and OpenSUSE 12.1 x64 and x32 will not boot... does anyone know what the major difference between these distros that will let some work but not others is?

Organized...
[QUOTE=The distributions that boot.]
Ubuntu 10.04.3 (x86/64) (Most likely Ubuntu 10.10 (x86/64) will boot, but haven't tested)
Debian 6.0.3 DVD (x86/x64)
ArchLinux (net-install)
Fedora 15 (x86/x64)
[/QUOTE]

[QUOTE=The distributions that don't boot.]
Ubuntu 11.10 (x86/x64) (Most likely that Ubuntu 11.04 (x86/64) won't boot, but haven't tested.)
LinuxMint 12 (x86/64)
LinuxMint Debian (x86/64)
OpenSUSE 12.1  (x86/64)
[/QUOTE]

---

### Post by TehSofaWolf on 2011-11-29
Bump. (I couldn't find anything about bumping in the rules, if it's disallowed, sorry)

---

### Post by TehSofaWolf on 2011-11-30
Bump. Could it possibly be the new Linux kernel?

---

### Post by tersogar on 2011-11-30
Bump!

---

### Post by TehSofaWolf on 2011-12-03
Bump. Pretty please? Would it be possible to put the HDD in another computer and install Ubuntu 11.10 on it?

---

### Post by Serpher on 2011-12-03
Your hardware is pretty new so it's quite common for the kernel not to support it 100% yet and that's when you can run into funky things like this. If you don't want to have to reinstall every 6 months, keep using Ubuntu 10.04. If you want something more cutting edge though you should use 11.10. If I were you I'd try running the 32-bit version of it and see if that will boot. Honestly you won't notice the difference. Also as a beginner I'd suggest sticking with Ubuntu or Linux Mint. Linux Mint basically IS Ubuntu, except for Linux Mint Debian which is Debian. Ubuntu is really only a modified version of Debian anyway. Debian though is very bare bones, it's for more advanced users. I used it once and honestly, they only use really old packages on the stable version of it so it feels like 2003 when you're using it. Arch Linux is good but then again you need a good understanding of what's going on to really appreciated it. Just stick with Ubuntu IMO unless you gain a lot of Linux knowledge and can develop a preference from there. If you don't have enough knowledge to develop a preference Ubuntu is probably for you.

For example I like CentOS best for what I use Linux for. I have a headless server (computer without a monitor) that sits beside my computer running Windows 7 (I game else it would be gone) and serves webpages, has FTP and SSH access. I'd hate Ubuntu for that lol.

---

### Post by TehSofaWolf on 2011-12-03
> **Serpher said:**
> Your hardware is pretty new so it's quite common for the kernel not to support it 100% yet and that's when you can run into funky things like this. If you don't want to have to reinstall every 6 months, keep using Ubuntu 10.04. If you want something more cutting edge though you should use 11.10. If I were you I'd try running the 32-bit version of it and see if that will boot. Honestly you won't notice the difference. Also as a beginner I'd suggest sticking with Ubuntu or Linux Mint. Linux Mint basically IS Ubuntu, except for Linux Mint Debian which is Debian. Ubuntu is really only a modified version of Debian anyway. Debian though is very bare bones, it's for more advanced users. I used it once and honestly, they only use really old packages on the stable version of it so it feels like 2003 when you're using it. Arch Linux is good but then again you need a good understanding of what's going on to really appreciated it. Just stick with Ubuntu IMO unless you gain a lot of Linux knowledge and can develop a preference from there. If you don't have enough knowledge to develop a preference Ubuntu is probably for you.

For example I like CentOS best for what I use Linux for. I have a headless server (computer without a monitor) that sits beside my computer running Windows 7 (I game else it would be gone) and serves webpages, has FTP and SSH access. I'd hate Ubuntu for that lol.

Thanks a ton for the answer. I normally run Debian Testing, but I used Ubuntu because 10.04 and 10.10 would boot but 11.04 and 11.10 wouldn't. I can't install 32-bit either, same thing happens. I just don't understand why an older kernel would work and a newer one wouldn't... maybe something to do with the power bug getting fixed?

---

