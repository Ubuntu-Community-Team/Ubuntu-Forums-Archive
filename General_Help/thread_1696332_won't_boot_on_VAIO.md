---
title: "won't boot on VAIO"
date: 2011-02-27
forum: General Help
---

### Post by Anton.one.two on 2011-02-27
I've been trying to install 10.10 on a 3 year old VAIO N Series, I've never done this before so this is my first experience with Ubuntu OS. I've been trying to boot from CD and USB Drive and changed the BIOS settings accordingly - boot order and enabled to boot from an external drive and still no luck. I think it is one of those weird Sony things, but it won't let me launch an ISO file before launching Windows. I'm running Vista Home Premium OEM, if this makes any difference. It recognizes the the installation when I burn the image or install it onto a USB, but won't let me boot from there.

Anybody knows how to deal with this? Would be greatly appreciated.

---

### Post by coffeecat on 2011-02-27
Ubuntu runs well, and Ubuntu live CDs boot OK, on my 2-year old Sony Vaio VGN-NS20S, so I doubt there's a "weird Sony thing" going on here. :)

Let's go back to basics. You've set the BIOS to boot from CD - good. How did you burn the ISO? What do you mean by:

> **Anton.one.two said:**
> it won't let me launch an ISO file before launching Windows.

Did you burn the ISO as an image to the CD? If you boot into Vista and insert the CD, does the Explorer window show a number of files and folders on the CD or just one very large .iso file?

---

### Post by Anton.one.two on 2011-02-27
> **coffeecat said:**
> Ubuntu runs well, and Ubuntu live CDs boot OK, on my 2-year old Sony Vaio VGN-NS20S, so I doubt there's a "weird Sony thing" going on here. :)

Let's go back to basics. You've set the BIOS to boot from CD - good. How did you burn the ISO? What do you mean by:



Did you burn the ISO as an image to the CD? If you boot into Vista and insert the CD, does the Explorer window show a number of files and folders on the CD or just one very large .iso file?

Thanks for the quick response. I burned the ISO as an image, tried both Nero 10.5 and InfraRecorder 0.51 using the "burn image" action with the latter. When I open "Computer" I see :"DVD RW Drive (F:) Install Ubuntu" and the Ubuntu installer logo. Double-click asks me for a permission from Vista to launch the installer and when I click "OK" - returns a "Windows - No Disk" error message. If I right click on the DVD Drive and press open, I see all the files and folders. Can this mean that the image did not burn properly? I've tried three times - twice with Nero and once with InfraRecorder.

---

### Post by coffeecat on 2011-02-27
If you see all the files and folders, then you've burnt the ISO properly. Some people make the mistake of burning the CD as an ordinary data CD, ending up with one huge 680MB or thereabouts file which, of course, won't do. I just wanted to check that point first.

When you try to run the Ubuntu installer from within Windows, you are attempting a Wubi install. This is where Ubuntu get installed to a virtual disk within the Windows C: partition. This is OK for a tryout, but has a number of disadvantages. More here:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

To install Ubuntu to its own partition so that it runs natively, you need to boot from the CD. Have you tried that? Put the CD in while you are in Vista and reboot. If the CD does not boot up, then something is wrong with it and we need to investigate further. Did you check the md5sum of the downloaded ISO? See here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you do manage to boot the 10.10 CD up, don't use the 'install alongside' option in the installer. There's a design fault in it and it has been known to destroy the Windows partition. If you manage to boot the CD, let us know, and someone can tell you what you need to do to avoid this.

---

