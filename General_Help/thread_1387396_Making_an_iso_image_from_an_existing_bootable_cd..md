---
title: "Making an iso image from an existing bootable cd."
date: 2010-01-21
forum: General Help
---

### Post by DeadlyOats on 2010-01-21
Hello, all you Linux gurus!

I have Ubunto 9.10, 64 bit version, installed on my laptop.  On my desktop it's the 32 bit version.

I have a Windows XP Pro Evaluation version that came with my MCSE 70-270 text book.  In my Windows 2000 install, on my desktop, I'm going to use MS Virual Machine to install the evaluation version of WinXP Pro.

Here is where I'm having difficulties.  I want to create an .iso file of the WinXP Pro Evaluation cd, and use the virtual cd drive, in the virtual machine, to mount the iso image.  That way I don't actually use the physical cd in my physical cd drive.

The problem is, I can't seem to make an iso image file from the cd.  I've read other posts here that suggest brassero and k3b, I have both, and have tried the suggestions.  The problem is that k3b does not seem to have an option to create an iso image from a bootable cd, and brassero only makes .bin and .toc file images.

What do I need to do to make a bootable iso image file from my WinXP Pro Evaluation cd - using Ubuntu.

Thanks.

---

### Post by flabdablet on 2010-01-21
Insert the CD into the drive. When the file browser window showing the CD's files appears, close it. Right-click the CD's desktop icon and select Copy Disc. In the Copy Disc dialog box, select Image File as the target to copy to. Then follow your nose.

---

### Post by warfacegod on 2010-01-21
In Brasero, you'll need to select Disc copy. In the CD/DVD Copy Options window that comes up, for Select a disc to write to select Image File. An image file is an .iso

---

### Post by DeadlyOats on 2010-01-22
Thanks for your responses, but as I stated above, brasero does not create an iso image file.  Brasero created two files, one called brasero.toc and one called brasero.toc.bin.

Right clicking the cd icon and clicking Disk Copy brings up Brasero with the same result.  A .toc and a .toc.bin files are made, not a .iso file.

I need an iso image file.  How do I get a .iso image file, based on the situation I described in my original post?

---

### Post by warfacegod on 2010-01-22
The instructions I detailed should have created an .iso, but since they didn't and you've already tried K3b, then the only thing I can say is give rubyripper a try. I don't think it's in the repo's so you'll need to find it online.

---

### Post by DeadlyOats on 2010-01-22
I stuck an Ubuntu 9.10 install cd, and followed your instructions, and got the same results.  Brasero does not give any other options except to save as a .toc and .toc.bin.  So, it isn't MS witchery messing with Linux, it's something else.

Am I missing a plugin or codec or something?

---

### Post by zircon214 on 2010-01-22
Insert the CD.

The disc will be auto mounted so first you need to unmount it, then copy the disc to a file.

```
sudo umount /dev/scd0
dd if=/dev/scd0 of=winxp.iso
```

---

### Post by warfacegod on 2010-01-22
Okay, I'm stumped. I just put a Window XP disc in my drive and got the same result. I doubt it's a codec issue because I've got lots of them, all sorts of restricted stuff installed and enabled. I dug around a bit and found this. Hope it helps.

[http://ubuntuforums.org/showthread.php?t=1386334&highlight=iso+rip]("http://ubuntuforums.org/showthread.php?t=1386334&highlight=iso+rip")

---

### Post by JiuJitsu500 on 2010-01-22
AcetoneISO??? I used it (I think warfacegod commented when i was asking about a better one a few days ago) to make plenty of ISO's, just straight images...

---

### Post by warfacegod on 2010-01-22
> **JiuJitsu500 said:**
> AcetoneISO??? I used it (I think warfacegod commented when i was asking about a better one a few days ago) to make plenty of ISO's, just straight images...

Sorry hoss, wasn't me, probably some other thread. Although, in a remarkable coincidence, that's the thread I just posted above.

---

### Post by DeadlyOats on 2010-01-23
Zircon214, your suggestion worked.  Thank you very much!  But I wonder why I had to do those "special" moves to get what I needed.  Why doesn't it work from the gui?

Thanks for your help, Warfacegod.  I will investigate your suggestion on that app, Acetone, for future reference.  But I wonder if Acetone has a feature that neither Brasero nor k3b has, and why is that?

---

### Post by flabdablet on 2010-01-23
You shouldn't have needed any special moves. From the behaviour you're describing, it looks like your source discs are being mis-identified as audio CD's. How many optical disc drives does your computer have?

---

### Post by flabdablet on 2010-01-23
Scratch that, I'm an idiot. Brasero does indeed default to making .toc/.bin copies. I knew there were good reasons why I tend to ignore Brasero.

But you should still be able to persuade it to make a .iso. If your Brasero disc copy window looks like mine, you should see a Properties button right next to the menu that lets you choose File Image as a copy target; click that, and you should see a file browser window that has an Image Type dropdown menu right near the bottom. Choose .iso off that and you should be good to go.

I have no idea why right-clicking on the disc icon and selecting Copy Disc gets you the idiot Brasero instead of Nautilus's rather nice inbuilt disc copier.

---

### Post by d3v1150m471c on 2010-01-23
Copy the .iso from the disk and then burn it as directed on the ubuntu website. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by warfacegod on 2010-01-23
> **DeadlyOats said:**
> Zircon214, your suggestion worked.  Thank you very much!  But I wonder why I had to do those "special" moves to get what I needed.  Why doesn't it work from the gui?

Thanks for your help, Warfacegod.  I will investigate your suggestion on that app, Acetone, for future reference.  But I wonder if Acetone has a feature that neither Brasero nor k3b has, and why is that?

I can't answer that. Every time I wanted to make an .iso I just used Brasero. Apparently that functionality has been removed in 9.10 for some obscure reason. I was never happy with the time Brasero took to make .iso's anyway. I'm gooing to use the command line from now on.

---

