---
title: "No sound in 10.4"
date: 2010-06-02
forum: General Help
---

### Post by Nick_Jinn on 2010-06-02
I cant figure it out. No sound at all. Anyone else experiencing this?

Its on a desktop and a laptop, both with entirely different hardware.

---

### Post by travlemon on 2010-06-02
> **Nick_Jinn said:**
> I cant figure it out. No sound at all. Anyone else experiencing this?

Its on a desktop and a laptop, both with entirely different hardware.

I'm still new to Ubuntu, but I'll try to help.  Are these new installations? Clean installations, or upgrades?  I would say make sure to use update manager to update your system fully.  Then also check to make sure the pulseaudio package is installed in Synaptic Package Manager. 

Let me know if that helps!

---

### Post by Nick_Jinn on 2010-06-02
Clean installation of lucid. These disks were recently burned.


Interestingly I had Lucid working last week. It must be something in the updates that is messing it up.

---

### Post by willygatti on 2010-06-02
Did you check to make sure your speakers are turned on, and your sound's not muted?

---

### Post by Nick_Jinn on 2010-06-02
lol
I am not a complete noob.


Laptop and desktop both have no sound after clean installation with the same disk that worked last week. I think it has to do with the updates.

---

### Post by lovinglinux on 2010-06-02
> **Nick_Jinn said:**
> lol
I am not a complete noob.


Laptop and desktop both have no sound after clean installation with the same disk that worked last week. I think it has to do with the updates.

You would be amazed how many people complain about sound issues to discover later that the PCM volume slider was half way down.

---

### Post by lidex on 2010-06-02
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by Nick_Jinn on 2010-06-04
Fixed on one computer. I will have to report back and see if its true with the other.

---

### Post by Nick_Jinn on 2010-06-06
The problem is a corrupted bios in the sound volume.

So how do I flash the bios from inside Ubuntu?

---

### Post by stderr on 2010-06-06
Huh? There's a BIOS on your motherboard, are you saying you flashed it recently? How you flash BIOSes depends on the motherboard model. 

Step back for a second - how did you fix the first PC, what's still wrong with the second, and why are we discussing BIOSes? :-k

---

### Post by Nick_Jinn on 2010-06-06
> **stderr said:**
> Huh? There's a BIOS on your motherboard, are you saying you flashed it recently? How you flash BIOSes depends on the motherboard model. 

Step back for a second - how did you fix the first PC, what's still wrong with the second, and why are we discussing BIOSes? :-k


I know for a fact that the volume is corrupted on the bios. I know because when I went to reinstall windows 7 it wouldnt let me finish because it said the volume bios was corrupted and it could not finish the installation on disk 2.

I am 100% sure beyond any shred of doubt that the bios is corrupted. I dont know how or why, but it is.

On the other PC I upgraded the bios but I had windows on that computer so it went smoothly. I dont know if it was caused by the same thing or not.



Its not the volume controls and its not the hardware. Its the bios. It really is.


Since its the bios, how do I flash the motherboard from inside Ubuntu?

---

### Post by stderr on 2010-06-06
The BIOS largely routes signals to and from peripheral and intergrated devices (ie integrated sound cards, onboard sounds cards, etc). The only really significant BIOS settings for audio are usually to do with disabling/enabling onboard audio, and more recently for codec selection. It may be that you have old BIOS firmware versions, and that flashing to newer versions may solve some bugs, but I don't understand quite what you mean when you say "volume is corrupted on the bios". 

Anywho, the procedure for flashing BIOSes is simple: you visit the website of your motherboard manufacturer, click on Support, Drivers, ... search for your model and download the BIOS files. They will always tend to release a version you can burn to floppy, CD, USB etc, and they sometimes offer applications you can run from within an OS (usually Winblows) too. I prefer floppy/CD/USB methods - more direct, less to go wrong.

---

### Post by Nick_Jinn on 2010-06-06
It really is the bios. I dont know how, and I dont remember the exact words but it told me that the volume file on the bios didnt exist, or something like that.




Here is the message I get when I try to execute the bios flash.


Do I have to put it on a disk and restart the computer to flash it?

---

### Post by stderr on 2010-06-06
Yeah that's the usual method, but it depends somewhat on which format your motherboard manufacturer gives you the BIOS file and flashing software. If you need some help flashing the BIOS, try to link us to the file you're downloading so we can see what the situation is.

Cheers

---

### Post by Nick_Jinn on 2010-06-06
There is no direct link, but you can find it here.

[http://gd.panam.acer.com/home/](http://gd.panam.acer.com/home/)


Notebook >
Aspire>
4540
Bios

It says error 1005, no file system for volume. Volume may be corrupted.

I used a different HD and it didnt help.



So I have a corrupted volume and I am having a hell of a time trying to fix it.

---

### Post by Nick_Jinn on 2010-06-06
I dont know if this helps, but its what I get when I try to execute from in Ubuntu.




Archive:  /tmp/.fr-LzqLyD/BIOS_ACER_1.03_Windows_AS4540/NBLG103.exe
[/tmp/.fr-LzqLyD/BIOS_ACER_1.03_Windows_AS4540/NBLG103.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/.fr-LzqLyD/BIOS_ACER_1.03_Windows_AS4540/NBLG103.exe or
          /tmp/.fr-LzqLyD/BIOS_ACER_1.03_Windows_AS4540/NBLG103.exe.zip, and cannot find /tmp/.fr-LzqLyD/BIOS_ACER_1.03_Windows_AS4540/NBLG103.exe.ZIP, period.

---

### Post by lidex on 2010-06-07
Yeah, you can't run that from linux. You'll need to boot into DOS. Check out the readme file in that archive and this page should get you going:
[http://taint.org/2007/04/23/153737a.html]("http://taint.org/2007/04/23/153737a.html")

---

