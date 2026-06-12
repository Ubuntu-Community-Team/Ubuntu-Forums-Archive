---
title: "CD written in Linux wont open in windows XP"
date: 2010-10-13
forum: General Help
---

### Post by peliroja on 2010-10-13
I have written a cd with photos and dvd in Linux and then I tried opening in windows xp but it didn't. It says that it is unable to read it.what can I do?

---

### Post by ubunterooster on 2010-10-13
If it the same computer can ubuntu copy the pictures to the XP partition?

I would see if the CD can be read in Ubuntu to check if all you did was make a coaster; we all do that at times

---

### Post by peliroja on 2010-10-13
a coaster?what is it?I dont have partition and I tried to open it in a different cd

---

### Post by irv on 2010-10-13
> **peliroja said:**
> a coaster?what is it?I dont have partition and I tried to open it in a different cd

He was making a joke: a coaster is something you put a glass or cup on when you set it on your coffee table so it don't leave a water ring stain.
If you go to the place menu when you are in Ubuntu it should have your windows partition listed. Just look for the size of your windows partition and go by that because it won't have the name of windows.

---

### Post by waltercool on 2010-10-13
Sounds like Rock Ridge... try burning your CD using Joliet (for Windows/Linux). I prefer Rock Ridge anyways

---

### Post by irv on 2010-10-13
> **waltercool said:**
> Sounds like Rock Ridge... try burning your CD using Joliet (for Windows/Linux). I prefer Rock Ridge anyways

I use K3B in Linux and never had a problem reading CD/DVD's

---

### Post by srs5694 on 2010-10-13
The use (or not) of Rock Ridge should be irrelevant; Rock Ridge is just a set of extensions to ISO-9660, which is the real filesystem used on most CDs. If an OS or program (such as Windows) can't understand Rock Ridge on a Rock Ridge CD, you should still be able to see the files, just with shorter filenames. Joliet is used much like Rock Ridge, but it's the "Windows-native" way to produce long filenames on CDs, vs. the Unix-centric Rock Ridge. You can use either one alone, both together, or neither.

The error message reported makes me think that the disc was a bad burn, as others have suggested, or possibly that there's a drive-to-drive or drive-to-disc incompatibility, if the disc is being read on a computer other than the one that created it. There's a slim chance that the disc uses some more exotic filesystem. Typing "sudo blkid /dev/dvd" (or whatever the CD/DVD drive's device filename is) in Linux should identify it, as in:

```

$ sudo blkid /dev/dvd
/dev/dvd: LABEL="livecd 2010070507:53" TYPE="iso9660"

```

If the TYPE is something other than "iso9660", it could be the disc uses a weird filesystem.

---

