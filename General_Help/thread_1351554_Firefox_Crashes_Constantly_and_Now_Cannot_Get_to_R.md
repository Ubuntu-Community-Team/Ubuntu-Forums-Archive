---
title: "Firefox Crashes Constantly and Now Cannot Get to Run"
date: 2009-12-10
forum: General Help
---

### Post by Acreo Aeneas on 2009-12-10
Okay, I installed a fresh copy of Ubuntu 9.10 on this system last night and now I can't get Firefox to run without crashing every time I open a new page or just even start the browser.

I got so frustrated, I did 
```
sudo apt-get install firefox
```

which installed the latest 3.5.5 (9.10 had 3.5.3).  Anyways, now I can't even get Firefox to open.  I've run Firefox through terminal and get this error in return:
```
Bus error
```

I've tried uninstalling Firefox using
```
sudo apt-get remove --purge firefox
```

Then did
```
sudo apt-get install firefox
```

I still get the "bus error" when I try and start Firefox through console.

I'm totally frustrated right now.  I don't know where to go from here.  I currently am using Opera in Firefox's stead until I can get it working again.

For reference, this rig's specs:

ECS KN1 SLI Lite Motherboard
AMD Athlon 64 3500+
2 x 512 MB DDR400 RAM
160 GB Hitachi SATA HDD
256 MB eVGA 7800GT (PCI-E)
DVD-ROM, DVD Burner
Ubuntu 9.10

I would like to FF working as this rig is going to be mainly used by my dad and he doesn't like changing to a new browser after recently getting used to FF's interface.

---

### Post by gslug79 on 2009-12-10
Totally random thought and probably wrong, but maybe worth a try. Did you do a completely clean install, or did you keep you existing /home partition? If the latter is the case, then your old Firefox configuration and extensions will still be there in /home/username/.mozilla. Try renaming this folder and see if it has any effect.

As I said, I'm probably wrong, but there may be some old extensions or settings that don't play nicely with a newer version of Firefox.

---

### Post by Acreo Aeneas on 2009-12-11
It's a totally clean install.  I previously had Windows XP on the system, but then I wiped it and tried to get Fedora 12 working.  After several days of frustration, I put Ubuntu 9.10 on there.

Everything else is stable except for Firefox which refuses to work.


On a side matter, I put a fresh install of Windows XP on another partition on the hard drive, but how do I go about getting GRUB to see the new XP partition and give me the option of choosing between Ubuntu and XP?  

Right now, the system boots straight into XP and GRUB menu never comes up.

---

### Post by Silent Warrior on 2009-12-11
There should be a couple of good tutorials about doing that. They shouldn't be hard to find - do a search. :P They should also include instructions on what to do in your situation. (Ideally you'd install Windows first, and THEN Linux to avoid it.)

See, Windows likes to overwrite GRUB.

---

### Post by Acreo Aeneas on 2009-12-11
> **Silent Warrior said:**
> There should be a couple of good tutorials about doing that. They shouldn't be hard to find - do a search. :P They should also include instructions on what to do in your situation. (Ideally you'd install Windows first, and THEN Linux to avoid it.)

See, Windows likes to overwrite GRUB.

So I seemed to have figured out.  ;)  Unfortunately, I was in a bit of a hurry and didn't bother using Gparted on my hard drive before I ran the Fedora 12 install.   So while I'm frustrating over getting Linux on this old computer working, my dad has been complaining left-and-right about not having Firefox and how he doesn't like this "Windows" (since he still fails at grasping the term "operating system"), and so forth.  So I was rather forced into putting XP back on another partion AFTER having Ubuntu installed first.

I'll look for the tutorials then.

Anyone else experience this problem before (the FF crashing one/bus error) that could shed some light on how may go about solving this issue?

---

### Post by john newbuntu on 2009-12-11
Just worth a shot, remove Firefox using Synaptic package manager.  Add this line to 
settings->repositories->other software->add:
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
Then hit reload and reinstall firefox 3.5.7

---

### Post by Acreo Aeneas on 2009-12-12
Okay, this is extremely frustrating...

I found **[this tutorial]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")** on getting GRUB working again with my XP installed after Ubuntu.

Except the first part of the tutorial is:

```
sudo grub
```Terminal returns:

```
command not found
```So how the heck do I enter GRUB then to turn it back on if Live Ubuntu doesn't recognize the grub command?

Oh great...I tried the second part just now...and I end up opening up a empty file.  There's nothing there in GEdit.

Now what?

---

### Post by john newbuntu on 2009-12-12
Look at this thread and follow step number 12 towards the middle of the page:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Ordes on 2009-12-12
Editing the menu.lst wont help you. When you fresh installed Ubu 9.10 you using grub2, and the method in the tutorial is for the older grub.

1. For reinstalling grub2 i found this document pretty helpfull. Use a LiveCd to boot up ubu, and than try method 2. As it is basiclly done through the gui 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)


2. About WinXP. When you install Win after Ubu, Windows will overwrite your bootloader (grub), and therefore you will always boot directly into Win. In the old grub u just had to reinstall grub and edit the menu.lst.
Grub2 is new, and i am new to grub2 too. But for me when i installed it (after the upgarde) grub2 was scanning the discs, locating the OSs, and auto creating the menu.

3. Firefox.
Did you setup profile for firefox? My friend once setup firefox profile by using "sudo firefox -profilemanager" , the result was his profile had been "root:root", and therefore firefox wouldnt really start or crash. This might not be the problem just an idea what is possible. In case you did sth like this you just have reset your ff-profile folder by "sudo chown -R user:user /ff-profile-folder"

For other people this did work:
[http://ubuntuforums.org/showthread.php?p=7173737](http://ubuntuforums.org/showthread.php?p=7173737)

__________________
[COLOR="Blue"]To mark your thread as[/COLOR] [COLOR="Gray"][SOLVED][/COLOR], use [COLOR="Red"]Thread Tools[/COLOR].

---

### Post by Acreo Aeneas on 2009-12-13
Oh, didn't know 9.10 used a new version of GRUB.  Explains why I couldn't follow the tutorial.  Thanks Ordes.  I'll try linked-to tutorial in the morning.  Hopefully it'll work and I can get GRUB going again.  :)

---

### Post by Acreo Aeneas on 2009-12-13
:popcorn:  Works like a charm, now GRUB is working again.  Thanks Ordes and John!

Now I just need to try your suggestion for Firefox (the linked-to one) to see if it works.

---

### Post by Acreo Aeneas on 2009-12-14
Okay, I tried the linked-to thread (last two posts), but it's still a no-go.  I still get a "bus error" when I try running Firefox through terminal.

This is the only computer out of 4 computers that I've had/have Ubuntu running on that's had this problem with FF.  

I'm going to list the PC's specs in case something there might be a cause:

ECS KN1 SLI Lite Mobo
AMD Athlon 64 3500+
2 x 512 MB of DDR400 (Kingston HyperX)
eVGA GeForce 7800GT
160 GB SATA HDD
Integrated Audio
DVD ROM, DVD Burner

---

