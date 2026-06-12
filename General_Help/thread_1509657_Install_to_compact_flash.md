---
title: "Install to compact flash"
date: 2010-06-14
forum: General Help
---

### Post by Cardale on 2010-06-14
I have a little computer I am trying to install ubuntu server 32bit on.

[http://www.termtek.com.tw/Product/ThinClient/TK-3550.htm](http://www.termtek.com.tw/Product/ThinClient/TK-3550.htm)

I am running into drive write issues.  Can anyone help....very very much appreciated.

---

### Post by Cardale on 2010-06-14
I have tried installing several different ways and the drive is never detected.

---

### Post by Cardale on 2010-06-14
Do I have to go with a different os?

---

### Post by Cardale on 2010-06-14
its i586 cpu.

---

### Post by snowpine on 2010-06-14
Hi Cardale, sorry nobody has answered your question yet, but you'll have to be more specific than "I am running into drive write issues." Please let us know what you've tried and the specific error messages you're getting. Posting the specs of your hardware may also help the experts of Ubuntuforums to assist you.

In the meantime, you might take a look at [the Ubuntu hardware requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu%20Server%20%28CLI%29%20Installation") to see if your computer meets them.

---

### Post by Cardale on 2010-06-14
Thanks for your comment.  The first post I made linked to the whole specs for anyone to help me out with.

Ubuntu Server isn't detecting the compact flash hard drive.  I have tried several different methods and I don't know what to do.

Once I get to the point where it says choose Partition it gives me nothing.  I have no available discs.

I am guessing this has something to do with embedded systems.  I also tried Ubuntu Desktop and when I get to the prepare partitions menu it displays no drives.

I am using a 4gb compact flash and I believe Ubuntu is having problems with the CPU or recognizing the hard drive, but I don't know.

Let me know if you need to know more.

---

### Post by snowpine on 2010-06-14
Do I understand correctly that you can boot the Ubuntu Desktop Live CD? That is a good start.

A good next step is to find out whether Linux can "see" the drive with the following terminal command:

```
sudo fdisk -l
```

---

### Post by Cardale on 2010-06-14
I ran that and it only listed the thumb drive and not the compact flash.

---

### Post by snowpine on 2010-06-14
> **Cardale said:**
> I ran that and it only listed the thumb drive and not the compact flash.

So the next step is to figure out why your compact flash card reader is not recognized by Linux. I am not an expert on this but I have seen successful how-tos on these forums. There is hope. :)

---

### Post by Cardale on 2010-06-15
I put my compact flash card into my desktop system that runs ubuntu desktop and created a start up disc of ubuntu server and put the compact flash card onto the thin-client and it didn't work.

When I did that it kept saying it couldn't find a cd-rom drive or drivers.

I also tried using a thumb drive and then I get the other error saying that a root wasn't defined, but then I never get any options to set my compact flash card as the root.

So I don't know.  The only thing I can think of now is some how installing via PXE, or some other method.

I would really like to get this working.  Would save on my electric bill :D

---

### Post by Cardale on 2010-06-15
still trying.

---

### Post by Cardale on 2010-06-17
Well after trial and trial and trial I have tried almost everything it seems as far as hardware switching goes.

I managed to get the device to install when I used 2 usb flash drives.  One as my "cd" and one as my "hard disk" once I managed to get this working I used dd and copied the partition to the compact flash drive which is the same size as the flash drive and it doesn't work.

Keeps asking for a PXE room...I don't know.  The client isn't supported any more so this is likely the only resource for support.

Let me know if anyone has any ideas because so far I haven't been able to boot any OS other than a live version.

---

### Post by C.S.Cameron on 2010-06-17
Does the CF show up in BIOS?
My laptop BIOS does not see CF as a hard disk.
It boots from flash drive fine though.

---

