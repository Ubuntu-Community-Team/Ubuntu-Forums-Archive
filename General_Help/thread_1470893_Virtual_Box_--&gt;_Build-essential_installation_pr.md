---
title: "Virtual Box --&gt; Build-essential installation problem"
date: 2010-05-03
forum: General Help
---

### Post by TheSkid on 2010-05-03
Hello.

I installed ubuntu on my laptop as virtualbox application.
I have tried to install build-essential like that command:
```
sudo apt-get install build-essential
```

If i do, i got the following message:
```
Media change: please insert the disc labeled 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)' in the drive '/cdrom/' and press enter
```.

If i insert the disc with the ubuntu-image and press enter, i see this message every time i press enter.
I looked in my Places folder, i saw my disc with the Label "Ubuntu 9.04 i386", but the terminal don't use the right path, i think.

Anyone has an idea how to solve this problem ?

Thank you and regards,
SkiD.

---

### Post by dino99 on 2010-05-03
as ubuntu is installed inside virtualbox (with its image) you need to give the cd path inside virtualbox, not the hardware reader.

---

### Post by TheSkid on 2010-05-03
> **dino99 said:**
> as ubuntu is installed inside virtualbox (with its image) you need to give the cd path inside virtualbox, not the hardware reader.

Thanks for your reply!

Can you tell me how i can do this ?
Or where can i read how i can give the cd path inside virtualbox ?

---

### Post by plucky on 2010-05-03
> **TheSkid said:**
> Thanks for your reply!

Can you tell me how i can do this ?
Or where can i read how i can give the cd path inside virtualbox ?

**Devices > CD/DVD Devices > Host Drive** and tick the box.

Do you have an internet connection in virtual box?

If so open **System > Administration  > Software Sources** and un-tick the box for the CD rom drive as a source.Then reload and try the install again from the repositories.


Good Luck

---

