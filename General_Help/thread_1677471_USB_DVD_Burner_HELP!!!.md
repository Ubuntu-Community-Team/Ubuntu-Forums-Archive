---
title: "USB DVD Burner HELP!!!"
date: 2011-01-28
forum: General Help
---

### Post by rebman on 2011-01-28
I am trying to burn an .iso but Ubuntu won't see my burner at all.. 

Newb to ubuntu, I am on 10.10

any help would be great!

Thanks

---

### Post by Habitual on 2011-01-28
What program are you using to burn?

---

### Post by rebman on 2011-01-29
I am trying to burn an .iso.

I right click the iso file and selected Write to disc. 

but no burner is seen.. The dvd burner is seen when there is no disc in it (in computer) but as soon as I put a disc in it disappears completely..

---

### Post by TheHackOps on 2011-01-29
Random idea that might work (Worked for me so hell why not)

Open Terminal (Menu > Accessories > Terminal) And type sudo mount -a

try it with the cd in also

---

### Post by rebman on 2011-01-29
> **TheHackOps said:**
> Random idea that might work (Worked for me so hell why not)

Open Terminal (Menu > Accessories > Terminal) And type sudo mount -a

try it with the cd in also

Tried it, no luck... 

This is driving me nuts! :)

---

### Post by TheHackOps on 2011-01-29
Model of CD Drive? Ill do some research

---

### Post by rebman on 2011-01-29
> **TheHackOps said:**
> Model of CD Drive? Ill do some research

Cool, thanks!

It is a Memorex DVD±R/RW/RAM DRIVE
Model Number: MRX-530L

---

### Post by ronnielsen1 on 2011-01-29
> So far all i get is this thing is "The most problematic piece of ****  ever" still looking though oh btw people have trouble with it on ALL  O/Ses so don't be bitching about ubuntu later when i can't find a holly  grail solution 	

:P

I've never had a Memorex drive but I've learned to stay away from their rewritable disks. If you have the option to return this, I would. It's a 

> piece of ****
[http://www.linuxine.com/story/unable-intall-fedora-12-duo-boot-windows-xp](http://www.linuxine.com/story/unable-intall-fedora-12-duo-boot-windows-xp)
[http://www.linuxine.com/story/fedora-10-checks-dvd-ok-cant-see-it-after](http://www.linuxine.com/story/fedora-10-checks-dvd-ok-cant-see-it-after)
> [http://forums.fedoraforum.org](http://forums.fedoraforum.org) –                   Hello, I downloaded the Fedora 10 DVD installation image and burn it to a DVD.The image was good, I checked  the md5 sum.When I put the DVD in the drive and rebooted the text based  menu appeared and I chose Install or upgrade.The the installer asked me  if I want to check the DVD and I entered Yes.The DVD was checked and it  turned out to be fine, but after that when I wanted to continue whit  the installation the installer reinserted the DVD but it gave a message  saying that it can't find Fedora on any drive :).Even if just minutes  ago it verified the DVD for integrity.And then it ejected the DVD.If I  wanted to press F12 to continue it reinserted the DVD and gave the same  message.So I can't continue my installation. What can I do?? The DVD was fine as you can see, checked by me and by the installer  itself.Is the installer asking for a CD?? I thought the DVD was for  installing.And even better, that DVD was made whit the exact DVD writer  which I use for the installation.So it can't be any incompatibility  problem between different DVD ROMs or Writers. The DVD installation is very important to me, because on that computer there is no internet connection.So the DVD is a solution to install a lot of software and actually use that computer, since yum does not work. Thank you for your time.

---

### Post by ronnielsen1 on 2011-01-29
You could try gnomebaker or K3B, both installable through Synaptic or through apt-get and see if it makes a difference, but seriously I stay away from Memorex disks. There might be other people that have good luck with them. I don't

---

### Post by ronnielsen1 on 2011-01-29
TheHackOps or someone else might find something. Like I suggested try gnomebaker and K3B - see if they make a difference. Is taking it back for a different model an option?

---

### Post by TheHackOps on 2011-01-29
Moderator just had a super over reaction because i swore....

---

