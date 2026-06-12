---
title: "Somehow I broke grub, cant boot now"
date: 2010-11-02
forum: General Help
---

### Post by justinsn95 on 2010-11-02
Somehow I managed to break grub. I was working on my mom's computer for her, fixing her hard drive. Well I ended up having to take her hard drive out of her computer and put it in mine, just to get windows to install. I had to reinstall windows because it had some kind of file system error and wouldn't even boot. Before, I had a Windows 7 drive, an Ubuntu 10.04 drive, and a storage drive. I could select which drive I wanted to boot into with grub. 

Well once I reinstall XP on my mother's hard drive, and removed the drive to put it back in her computer, I can now no longer boot into any of my drives. I get some error message saying that grub has an error. It has some long list of characters after that, with a few dashes here and there in between them. And I can type something on this screen as well, although I have no idea what it wants me to type. 

How can I fix this? As it stands I am locked out of both my windows 7 drive, and my linux drive. This really sucks lol.

---

### Post by Swagman on 2010-11-02
Sounds like your  bios has adjusted itself to the new parameters (your mums drive).

go back into bios and rescan hard drives. Then save out.

---

### Post by oldfred on 2010-11-02
Did you switch drives, so BIOS is booting wrong drive that does not have good version of grub?

IF not then run this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by justinsn95 on 2011-11-24
Unfortunately I am having this same problem again. I had Ubuntu on a separate drive. But then I removed the drive and reformatted it to serve in another computer. But now somehow, I'm still stuck with grub. And instead of booting right into windows like its supposed to, it says 

"Verifying DMI Pool data:..................error: No such device: (very long string of incomprehensible characters) grub rescue>_"

---

