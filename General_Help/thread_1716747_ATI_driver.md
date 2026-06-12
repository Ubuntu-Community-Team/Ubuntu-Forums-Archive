---
title: "ATI driver"
date: 2011-03-28
forum: General Help
---

### Post by annirun on 2011-03-28
I've had a problem with multiple programs installed in wine that i'm fairly certain stem from my videocard's driver.  Unfortunately, the additional drivers menu shows no proprietary drivers.  it is a x1250 (integrated) and back when I used Windows the correct driver was [http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_xp.aspx](http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_xp.aspx)

How do i switch to another driver?

---

### Post by Katalog on 2011-03-28
This link should explain:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by annirun on 2011-03-28
thank you for the fast reply
```
sudo sh ati-driver-installer-11-2-x86.x86_64.run --listpkg
```
doesn't list maverick, is there another way or will i have to change linux distros/revert to ubuntu 9.04(which was listed)?

---

### Post by Krytarik on 2011-03-29
Unfortunately your card isn't covered by the proprietary driver anymore.  But it should nevertheless run fairly good with the Open Source Edge  driver:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```Greetings.

---

### Post by annirun on 2011-03-29
well that driver didn't work either...  I am trying to run Starcraft II in wine.

ACCESS_VIOLATION (0xC0000005)
occurred at 0073:06A055CB.  The memory at '0x48074F15' could not be written.

which is the same error i got when i tried WoW a while back and gave up after researching and being told it was a driver problem.

---

### Post by 3Miro on 2011-03-29
> **annirun said:**
> well that driver didn't work either...  I am trying to run Starcraft II in wine.

ACCESS_VIOLATION (0xC0000005)
occurred at 0073:06A055CB.  The memory at '0x48074F15' could not be written.

which is the same error i got when i tried WoW a while back and gave up after researching and being told it was a driver problem.

Starcraft II with wine on ATI (and an unsupported one), sorry to bring the bad news, but this will not work. I have Nvidia GTX260 with six core CPU and Starcraft II is barely playable on minimum settings.

---

### Post by annirun on 2011-03-29
:( all i wanted to do was join and leave games with a friends account so i can solo 2v2 matches on my desktop.  oh well this thing is getting kinda old anyways... maybe i should upgrade...

---

