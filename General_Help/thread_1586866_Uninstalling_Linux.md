---
title: "Uninstalling Linux"
date: 2010-10-02
forum: General Help
---

### Post by AbsoluTho on 2010-10-02
First, I'm not an english speaker so I apologise if I am a bit hard to understand.

My situation is as follows: I have a machine with Windows 7 Ultimate installed and I'd like to try Ubuntu. I am a bit weary of this because I've intalled Ubuntu once on a Vista machine and had problems uninstalling it. I just deleted Ubuntu's partition, but that resulted in something being corrupted during computer lauch. Long story short, I had to format my drive completely and reinstall Windows Vista.

I am trying multiple distributions of Linux and this time I absolutely cannot afford to lose my 7 installation, so I'd like to know if there is any way to unninstal Ubuntu after it being installed that doesn't imply reinstalling the Windows OS.

Many thanks in advance.

---

### Post by howefield on 2010-10-02
If your machine can handle running a Virtual Machine, then you could try running Ubuntu as a virtual machine.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

You could alternatively install a "Wubi" installation, whereby removal of Ubuntu would involve nothing more complicated than Add/Remove programs (or the equivalent control panel option in Windows 7)

[http://wubi-installer.org/](http://wubi-installer.org/)

Or you could install as you did previously but this time learn to restore the MBR.

---

### Post by AbsoluTho on 2010-10-02
Thanks for the help.
 
I have downloaded Wubi but after I execute it (with Administrator privileges) nothing happens whatsoever? I have looked into the Wubi FAQ and it doesn't mention any prerequesite programs, so I am at a bit of a loss here.

---

### Post by CiscoPenguin on 2010-10-02
Just run virtual box like stated in the post above, or just use a LIVE cd.

---

### Post by AbsoluTho on 2010-10-02
My computer doesn't support Virtual Machines. The live CD has the problem I explained in the first post. As for restoring the MBR I have [looked it up]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") but apparently it requires the Windows 7 CD which I don't have (came preinstalled with the machine). Though if a Windows Vista CD can be used to access the command prompt I have one available.

---

### Post by CiscoPenguin on 2010-10-02
Don't install the LIVE CD to your hard drive, just run it from the CD without modifying your disk.  In your first post you said that you installed it to your HDD.  Just run the LIVE environment if your just testing it out.

---

### Post by AbsoluTho on 2010-10-02
> **CiscoPenguin said:**
> Don't install the LIVE CD to your hard drive, just run it from the CD without modifying your disk. In your first post you said that you installed it to your HDD. Just run the LIVE environment if your just testing it out.
 Sorry, should have explained that I would be testing it a bit more deeply, so I'd prefer if I could just have a normal installation but knowing a way to restore my machine to pre linux if needed. I am actually typing this from Ubuntu running on a flash drive.

---

### Post by ajgreeny on 2010-10-02
You can also repair the windows7 MBR using a software download of EasyBCD from [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

