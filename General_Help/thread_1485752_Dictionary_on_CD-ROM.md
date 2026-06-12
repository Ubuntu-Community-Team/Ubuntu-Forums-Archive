---
title: "Dictionary on CD-ROM"
date: 2010-05-17
forum: General Help
---

### Post by WDYSUN on 2010-05-17
Dear all,

I have a dictionary on a CD-rom which worked under Win xp, there is any way to use it under linux? I tried with Wine but it didn't work (some dll where missing).

I wonder whether there exits any way to mount the cd-rom on a virtual driver in order to use it on the Karmic.

Best 
Pietro

---

### Post by 3rdalbum on 2010-05-17
You just put the CD-ROM in and it will mount on Ubuntu, then you can attempt to "install" it on Wine. This will put the DLLs where they should be.

Some of those dictionary CD-ROMs actually consist of HTML files which of course you can read on Ubuntu.

---

### Post by WorMzy on 2010-05-17
Ubuntu has it's own dictionary application if you look under Applications -> Office -> Dictionary. I believe it requires an internet connection though, so it might not be useful for you.

---

### Post by mikechant on 2010-05-17
For windows supplied dlls, if you've still got the Win XP install you can copy them from there. You will probably find the dll in C:\WINDOWS\system32 and should be able to copy it to the wine equivalent - ~/.wine/drive_c/WINDOWS/system32

(This is from memory, I'm at work with no Ubuntu access at present)

If this doesn't work maybe give us the name of the missing dll.

---

