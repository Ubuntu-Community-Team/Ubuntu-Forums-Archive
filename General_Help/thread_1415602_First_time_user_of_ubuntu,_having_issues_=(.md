---
title: "First time user of ubuntu, having issues =("
date: 2010-02-25
forum: General Help
---

### Post by slick slab mcknab on 2010-02-25
Sort of.....

The short of it...My Vista machine refuses to boot after the installation of a service pack update. It just hangs at the "loading bar" thing. No safe mode load ups, with or without networking. So I want to reformat, but first I want to recover some files. 

Download Ubuntu 9.10 and slap it on a USB thumbdrive with the fedora liveusb creator. Problem is that my machine gives me a "Boot Error" and doesn't do anything. This also happened with centos. I tried ubuntu on my XP machine and it worked flawlessly, even played some rounds of worms! lol. 

My Vista machine is using a Core 2 Duo Quad Core (Q6600) and I guess is a 64 something processor, dunno how all that works. Is there a specific version that I need to use? Or any little trick I could do? Thanks for any help in advance! =)

Ian

---

### Post by mörgæs on 2010-02-25
You should be able to use any Ubuntu for booting. 

Does the Vista machine boot from an Ubuntu CD? To be absolutely sure, you could try 9.04:
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by jblaven on 2010-02-25
Does your computer give you a boot error when trying to boot even into Vista (even without the thumb drive inserted)?

---

### Post by PoHandle on 2010-02-25
I'd recommend you take a look at your BIOS settings as well.  Though I'm sure your computer will support, booting from a USB stick, it's always good to double check.  You could also find out if there are other settings regarding a boot from USB.

---

### Post by jblaven on 2010-02-25
> **PoHandle said:**
> I'd recommend you take a look at your BIOS settings as well.  Though I'm sure your computer will support, booting from a USB stick, it's always good to double check.  You could also find out if there are other settings regarding a boot from USB.

Yep, that's what I was wondering...

---

### Post by ndefontenay on 2010-02-25
I can never manage to boot from USB. CD is my prefered solution.

What you could do is use a live CD session of linux to copy your data from vista to some external hard drive. Then you can just do whatever you want. Erase the whole disk and go on linux and try dual booting first (even though it's not working, you can still access the data).

Nico

---

### Post by slick slab mcknab on 2010-02-26
Well, I re-read all the prompts that pop on for my bios on boot-up and i saw the line that says that my version only supports hdd and disc booting =( So that answers my usb dilemma. Gonna retry .10 on a disc and hope that it works. Which is weird cause in the settings it lists usb devices as a bootable option and recognizes the stick in the port and allows me to up the order. anywho, thanks for reminding me to actually check the options. =)

and jb:  I don't get an error with vista like i do with the usb stick, and i almost wish it did. but it'll start to boot up fine, but when it gets to the loading bar/status bar it'll hang there until i do a force shutdown. does the same for safe mode and won't let me get into anything. started doing this upon restart from a fresh install of sp1. =/ i heard something similar happening with xp on a recent update so im guessing the same thing is happening with vista.

---

### Post by slick slab mcknab on 2010-02-28
Just had one of those ah-ha! moments. XD went into c*usa to see about getting a sata-iede cable to pop my vista hdd to my xp machine which was booting ubuntu from usb and transfer that way. and i started talking to one of the guys and shooting the **** about how my bios won't let me boot from a THUMBDRIVE, and says it will boot only from hdd or cdrom. and he looks at me and goes, do you have an external usb hdd, either portable or not. and then i smirk, and think, son of a bitch. 

so i installed ubuntu onto my 40gb external portable usb hdd and have it working on my busted vista machine, can access my hard drive and transfer files. i completely forgot about external hdd options. maybe my brain fart will help someone else in the same dilemma. =P if it helps i did install 9.10 to the external. and more than likely i'll keep it on there for future use. and i'm guessing that the extra space on the drive is just like regular ole space to store pics/videos/music and whatnot, right?

Thanks for the assisst guys!

---

