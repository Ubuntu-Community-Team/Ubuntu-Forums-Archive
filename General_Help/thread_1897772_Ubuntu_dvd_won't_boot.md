---
title: "Ubuntu dvd won't boot"
date: 2011-12-19
forum: General Help
---

### Post by Bannabein on 2011-12-19
Hello.

I have just downloaded Ubuntu 11.10 64-bit, burnt it onto a DVD and behold: The DVD won't boot.

I've tried restarting, and I've tried pressing F2 at start-up for the boot menu, but the DVD won't even show up in the boot menu.

I've also tried the "help me boot from CD" option in the installer menu, but then I get this error:

"WindwosBackend object has no attribute 'cd_path'"


I am aware that this is a common problem, and people have probably asked the same question a million times before. I've read through many different forum posts on the matter, but no solution seems to fit my case:

- Yes, I do actually have a 64-bit computer

- No, the DVD is not corrupted 

- I already have disabled the wireless adapter, as windows 7 crashes anyways when there are wireless connections in the area (gotta love that!)

- Yes, I have tried accessing the boot menu manually (F2), but the Ubuntu DVD won't show up.

Edit

- Yes, I've burnt a proper image DVD. 


So what do I do now?

I'm running windows 7 on an Acer Aspire laptop, by the way.



Any help is much appreciated.

-Bannabein


EDIT:

Oh yeah, and I'm going for the dual boot option. I've already partitioned the hard drive. And yes, there is plenty of space.

---

### Post by Jdogzz on 2011-12-19
Did you try installing it with a flash drive, or an external hard drive if you have one to spare? I stopped using discs myself because it seems wasteful when I can use the same hard drive as many times as I want for whatever I want to boot with.

---

### Post by Buntumatic on 2011-12-19
Well, folks often burn the ISO image to DVD as a file. This will not be bootable. Did you burn it as an image?

---

### Post by Bannabein on 2011-12-19
> **Jdogzz said:**
> Did you try installing it with a flash drive, or an external hard drive if you have one to spare? I stopped using discs myself because it seems wasteful when I can use the same hard drive as many times as I want for whatever I want to boot with.

Thanks for the reply.

I don't have a flash-drive available right now. And besides, I thought you couldn't boot from a flash drive, or that it was unsafe or something. Something I picked up when doing emulation on my old mac, but maybe I'm outdated.

And besides, I'm kind of annoyed that it's not working and want to figure out why. Any suggestions? I've found tons of threads on the matter, so it must be a fairly common thing. But no decent answers so far, for my part at least.

Downloading Kubuntu now, to see if there's any difference. 

Oh, and by the way. I'm going for Linux because I want stability, just so sick of Windows 7 crashing on me all the time and support-staff having no clue what-so-ever.

So...what Linux distro would you recommend if stability is the main thing? So far I'm not impressed with Ubuntu :-)

---

### Post by Bannabein on 2011-12-19
> **Buntumatic said:**
> Well, folks often burn the ISO image to DVD as a file. This will not be bootable. Did you burn it as an image?

Oh yeah, I forgot to mention that:

Yes, I burned it as a proper disc image DVD.

---

### Post by QIII on 2011-12-19
Did you check the md5sum on the file you downloaded?

---

### Post by Bannabein on 2011-12-19
> **QIII said:**
> Did you check the md5sum on the file you downloaded?

Should this be a problem when I downloaded the file from the official Ubuntu homepage?

---

### Post by QIII on 2011-12-19
An error in transmission or copying the iso can, and does, happen from time to time.

---

### Post by killermist on 2011-12-19
I don't know that it is a problem in this case, but I will also generally check the md5sum of the burned disc against the .iso file to verify the burn.
```
md5sum /dev/dvd ubuntu-ver.name.iso
```
Which should output something like:
```
f0300dbabf71cddd2b7604c8c15054ec  /dev/dvd
f0300dbabf71cddd2b7604c8c15054ec  ubuntu-ver.name.iso
```
(where obviously the 2 sums should match)

---

### Post by Bannabein on 2011-12-19
> **QIII said:**
> An error in transmission or copying the iso can, and does, happen from time to time.

Thanks for the respons, and same goes to killermist.

I did verify the disc after burning, and got no error message.

Too bad I can't access the internet from my own computer + i don't have a memory stick to transfer over to the comp. Im using now.

Apparently, I can't do this thing natively in windows, so I need to download a program. Not possible right now.

The error message I'm getting should mean something though, but I haven't found an answer to that anywhere.

---

### Post by QIII on 2011-12-19
Natively in Windows?

Ubuntu is not installed as a "program" per se.  It can be installed "in  Windows" using Wubi, if that is what you are trying to do.

For that, you will need the Wubi installer

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Are you interested in installing it as a native dual-boot?  That is, NOT as a file folder in Windows?

---

### Post by Bannabein on 2011-12-20
> **QIII said:**
> Natively in Windows?

Ubuntu is not installed as a "program" per se.  It can be installed "in  Windows" using Wubi, if that is what you are trying to do.

For that, you will need the Wubi installer

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Are you interested in installing it as a native dual-boot?  That is, NOT as a file folder in Windows?

No no, I meant I can't check the md5sum of files natively in windows. You need an external program for that, which I can't download right now.

I want to install Ubuntu as dual boot with windows, yes.

---

### Post by killermist on 2011-12-20
What you might try so you can get at all the tools/toys Linux has quickly, maybe start with a x86/32 bit version (fully knowing that it won't take "full advantage" of a 64 bit chip and possibly not use all the memory) and then upgrade to 64 bit once you're more comfortable.
This gives you the opportunity to start from a solid environment with all the tools you need while trying to troubleshoot what is (or isn't) working in trying to burn/boot the x64 disc.

If you've got multiple optical drives, I would recommend using KNOPPIX as a live environment in which to dabble while still being able to burn discs and such, and then work "up" from there as to booting and installing what you plan to use over the long term.

[edit]
I understand that this probably isn't an immediately useful suggestion, but getting into Linux isn't often an over-night kind of exercise.  It took me quite some time to get into Linux.
KNOPPIX really won me over (as a live CD) by allowing me to do web banking easily at a time when Win2k wanted to be a ... unmentionable ... with the time taken to install, then all the necessary updates.

---

### Post by QIII on 2011-12-20
Ah.

OK.  The md5sum check is the first step before you throw your hands up.

If you can't download it right now, the next best thing (aarrrgghhh!)  would be to download the .iso again just to be sure, burn it as an .iso  again just to be sure (burn at the slowest speed possible, by the way)  and give it a whirl again.

But then, if you can't download a native Windows tool for doing the  md5sum check, I suppose it would be difficult to download the .iso, eh?

And while we are at it...

Is your motherboard new enough that it is using a UEFI instead of a BIOS, and is that UEFI one that comes from an OEM that bows to the demands of the Temple of Redmond and the Microsoft "secure booting" scheme?

---

### Post by xc3RnbFO8P on 2011-12-20
I had similar problem yesterday, I could hear the dvd spinning but black screen.
The solution for my was to press (many times) F10 after the bios splash screen,
then I did F6 and choose **nomodeset**  to start the live disk

---

### Post by Bannabein on 2011-12-21
Thanks for all the help, good people.

I ended up driving home to get my USB stick, and then everything worked out just fine. 

Absolutely beautiful OS. Tidy and nice. Exactly what I've been missing since I made the switch from Mac to PC. 

And guess what? I doesn't even crash because of too many wireless networks in the area!

Hooray! (and goodbye to Windows 7)

---

