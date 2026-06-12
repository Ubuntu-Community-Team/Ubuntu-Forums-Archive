---
title: "Cannot write to USB thumb drives any more"
date: 2010-06-18
forum: General Help
---

### Post by rdbowers on 2010-06-18
I was able to read and write to my USB thumb drives until I mounted a USB thumb drive with an autoinstaller, and every since then all of my flash drives show up with the owner as "root".  I've tried changing the owner, and I'm not allowed- even with using sudo chown.

I don't get an error with that, but the owner isn't changed.  I can read from the drives but not write to them.  (I found that I can copy to the flash drive by using sudo cp, but I want to get away from command line stuff.  I have too much to do to be constantly dropping into terminal mode!)

I had no problems until the very minute I mounted that flash drive.

I've read a few threads, and found other people with symptoms similar to mine, but when I try the fixes suggested, they didn't work.

I've also not been able to locate anything that the flash drive autoinstaller changed or put in, but I must admit that I still am a relative newbie to Linux (been around computers since the early 70's, around Windows since 92-93, around OS/2 94-96, and Linux for only a year or so- and haven't learned that much command line stuff yet!).

I've been fighting this problem for a couple of weeks now, and it's causing me headaches!!!

---

### Post by rdbowers on 2010-06-19
Another strange symptom:

With a thumb drive containing the autoinstaller (but it's supposed to be disabled) plugged in, my computer will not boot.

A thumb drive WITHOUT the autoinstaller- it boots OK.  No thumb drives- boots normally.

I didn't notice this until after the "original" thumb drive with an autoinstaller installed something.  I've done a virus scan- nothing found.

I'm getting more and more confused- I've not heard of this happening to anyone else.

---

### Post by Baneblade on 2010-06-24
I'm experiencing this too. It seems to be limited to flash memory however, as my USB external HDD's work just fine.
Having used a friends flash drive with that awful "U3" software on it seems to have brought on this flash/write issue.

After this occurred I figured it was just that particular drive, but after testing a camera SD card (which worked before) I think it has broken writing to all flash memory devices!

I no longer have access to the usb stick that seems to have caused this whole thing. 
OP, perhaps you could (with the media attached) run: 
```
ls -l /media
```

Something else that might help would be to run this after you have connected the device: 
```
dmesg
```

---

### Post by warfacegod on 2010-06-24
I'm not sure what this "Auto installer" is your talking about is but this is what I would do.

1. ```
sudo apt-get purge (package-name)
```

2. Use Gparted to format the flash drive

3. If necessary (automount isn't working) ```
sudo apt-get install ubuntu-desktop
```

I'm not sure which package or packages deal with automounting but that last code *will* pull them in.

---

### Post by rdbowers on 2010-06-24
Thanks for the replies!

Yeah, Baneblade, that is what happened to me too.  The V3 software.  I also figured out that I can no longer write to cards as well.

Warfacegod- I've not been able to figure out what was installed or changed.  I've spent hours trying to figure that out without luck.  I've tried uninstalling and reinstalling packages connected with mounting thumb drive, but to no avail.  

I can get information from /media (and tried to change ownership there), but it didn't work, dmesg also didn't give any information as to what might have been changed (everything there looked normal as far as I could tell- although I'm not a Linux guru, I could puzzle out a lot of what I saw).

I'm thinking about asking the manufacturer of the thumb drive to find the fix for me- after all, it was their V3 software that did it.

Oh... and before anyone tries to send me off on a wild goose chase reading thread after thread about V3, I've already been there.  I found no answers to this problem.

---

### Post by warfacegod on 2010-06-24
Did you search for V3 in Synaptic?

---

### Post by rdbowers on 2010-06-24
Yep, and looked at the software there.  Nothing there applies to the problem.  It's all for dealing with V3 software- such as removing it from firmware.

---

### Post by warfacegod on 2010-06-24
First of all, you'll never get chown to work on a flash drive that's got a Windows filesystem on it. Virtually all of them are FAT32 (I've seen a *few* that came as NTFS).

Have you tried 02. in my first post?

For the sake of clarity (not just my own), what exactly did you do that caused this? It sounds like you plugged in a jump drive with some pre-installed app or package or something. Then you'd said something about firmware.

---

### Post by rdbowers on 2010-06-24
I installed that package via synaptic a long time ago, uninstalled it to see if it had somehow become corrupted, and then re-installed it.

Automount seems to work fine.  The problem is you cannot write to the drives unless you go into terminal mode and do "sudo cp ...".

---

### Post by rdbowers on 2010-06-24
I also have not been able to change permissions.

---

### Post by Leppie on 2010-06-24
> **rdbowers said:**
> 
I've also not been able to locate anything that the flash drive autoinstaller changed or put in
could you explain what application this is exactly (name of the app and what it does)?

---

### Post by rdbowers on 2010-06-24
It's called V3, and it is a Windows App that installs software that is supposed to make things easier and quicker when you connect a flash drive containing it.

According to the IT people at my school, it is now the primary means of spreading viruses- hackers have figured out how to co-opt the autoinstaller.  It's in firmware in the thumb drive, and more about the structure or whatever I don't know.  They told me that whenever a thumb drive comes in that has the autoinstaller, they trash it unchecked or unopened (they said that the autoinstaller- V3 or whatever it's called- can bypass a lot of the protection in Windows computers- and maybe Linux now as well).

I do know that the software is supposed to be Windows-only.

---

### Post by Baneblade on 2010-06-24
It is "U3" both the company name, and the software. more [info here]("http://en.wikipedia.org/wiki/U3") if you don't know what it is.

I think the best thing to do is wipe the drives and just format them as regular FAT for cross platform use.

As for this write issue that it seems to have caused, i'm still looking for a fix.

---

### Post by rdbowers on 2010-06-24
Yeah... U3 instead of V3.  I don't know how I got them confused...

I will be eliminating that stuff from my flash drives, but it's a lower-priority item right now.  The write issue?  That is higher priority.

---

### Post by rdbowers on 2010-08-04
Problem found.  I'm not sure what it was, but doing a "reinstall" didn't fix anything (I tried reinstalling all of the USB software).  I completely removed "usbmount" today and rebooted the computer, and now the write-to-flash problem is gone.

I think I'd tried that before- but there have been updates to Ubuntu since then, and maybe that made the difference!!!!

---

### Post by wgbuntu on 2010-09-24
I had the same problem with a bootable usb thumb drive. Removing usbmount fixed the problem. Make sure that pmount is installed.

---

