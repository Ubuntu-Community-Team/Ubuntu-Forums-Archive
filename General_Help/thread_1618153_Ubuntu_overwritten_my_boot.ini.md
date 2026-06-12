---
title: "Ubuntu overwritten my boot.ini"
date: 2010-11-10
forum: General Help
---

### Post by michnl on 2010-11-10
Hi all, 

im new to these forums and just installed ubuntu on my 2nd harddrive where i ran into a problem booting back to windows.

When i boot from my 1st harddrive it starts up ubuntu and from my 2nd harddrive where its installed it says disk boot failure, the strange thing is, setup did not recognize my 1st drive (OCZ Vertex 1.5 SSD) but still it has overwritten my boot.ini with grub4dos.

Now this is not really a problem i could get my boot.ini working with help of xp setup but i would like to continue use ubuntu aswell, so my question is if someone could help me out with grub4dos setting it to boot windows from 1st hd and ubuntu from my 2nd hd. 

In the meantime, google is my friend, ima try and see what i can figure out myself.

Thanks in advance,

Michael.

---

### Post by searchfgold6789 on 2010-11-10
Why not just use regular GRUB2?
You can repair the boot.ini from the windows setup, and boot from the Live CD and in the terminal ```
sudo grub-install /dev/hda
```

---

### Post by michnl on 2010-11-10
Thanks for your quick response, i will be testing it as we speak :)

 Keeping u posted,

Michael

---

### Post by Mark Phelps on 2010-11-10
The only time you have GRUB4DOS is when you do an install using Wubi -- in which case, installing GRUB will not only do you no good, it will actually make things worse.

Also, from my experience, all that Wubi does with the boot.ini file is add an entry for Ubuntu to launch wubildr.  So, the original Windows entry (ies) should continue to work just fine.

---

### Post by michnl on 2010-11-10
Sorry guys, after mark helps post i think  i may have misinformed you, have windows 7 installed on hd1 and ubuntu on hd2.

with windows 7 no longer using a boot.ini instead it uses a bootmgr, wich i hope is still there, i see several files on the 100mb partition win7 made like grldr, bootmgr and bootsect.bak with 2 folders boot and system volume information.

---

### Post by michnl on 2010-11-10
would there be a way to get my bootmgr working along with the ubuntu boot loader currently installed?

---

### Post by michnl on 2010-11-10
I believe it boots from my ssd from this point of view:

[IMG]http://oi53.tinypic.com/2ius08z.jpg[/IMG]

---

### Post by michnl on 2010-11-10
I just installed startupmanager and it showed 4 options

Ubuntu
Ubuntu (Recovery)
Memtest 86+
Memtest 86+ (Serial)

Could i add my windows 7 to this list?

*Edit, i have grub2 installed. (Ubuntu 10.10)

---

### Post by dino99 on 2010-11-10
read how to make an install with ubuntu:

[http://ubuntuforums.org/showpost.php?p=10098366&postcount=2](http://ubuntuforums.org/showpost.php?p=10098366&postcount=2)

---

### Post by michnl on 2010-11-10
> **dino99 said:**
> read how to make an install with ubuntu:

[http://ubuntuforums.org/showpost.php?p=10098366&postcount=2](http://ubuntuforums.org/showpost.php?p=10098366&postcount=2)

Yes sir, i have.

Used unetbootin to create an usb setup for ubuntu 10.10, worked perfectly,

* I may believe that this is a bug in the installer where it installed the boot files on the wrong partition,

Currently i have my 2nd harddrive working with grub2 so i can fix the bootmgr on my windows 7 but id rather have them both in the same menu, by adding windows7 bootmgr to grub2 and boot from hd2 in bios with memtest aswell :D

---

### Post by michnl on 2010-11-10
Problem solved :)

I am now running in windows 7, followed a tutorial on how to create a new grub script wich added a new entry in my grub boot and the windows 7 bootmgr was still intact.

---

### Post by Mark Phelps on 2010-11-10
Glad to here you got it sorted.

My guess is that (1) you had the Win7 drive mounted when you installed Ubuntu to the other drive, and (2) Ubuntu installed GRUB to the Win7 drive -- by default.

In future, you can avoid this problem by doing what I do -- having only the drive connected to which I intend to install the OS.  This prevents accidentally installing stuff to the wrong drive.

It's a simple matter later to update grub to add entries for the other OS.  And, this leaves the Vista/Win7 boot loader and MBR stuff alone -- avoiding another source of problems.

---

