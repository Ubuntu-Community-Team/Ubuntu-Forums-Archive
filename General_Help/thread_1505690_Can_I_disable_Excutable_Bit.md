---
title: "Can I disable Excutable Bit?"
date: 2010-06-09
forum: General Help
---

### Post by Gondee on 2010-06-09
I have lightly used previous versions of Ubuntu, and this "feature" was not present. But now, with 10.04 i cant install the software I want to install. Namely Steam under Wine. I know I could do the play on linux deal, but I would really like to disable this "feature" entirely. 

Can I do that, and how?

---

### Post by pytheas22 on 2010-06-09
I agree that this feature is obnoxious and poorly implemented.  The easy way to get around it is to right-click on the .exe file you want to run, select "Open with Other Application..." and then enter "wine" in the box labeled "Use a custom command."  This bypasses the utility that throws a warning about the executable bit.

You could also probably just edit the script at /usr/bin/cautious-launcher (which is what actually gets called when you try to open .exe files) to prevent it from doing anything, but I haven't tried that yet.

---

### Post by jerome1232 on 2010-06-09
or you could just set the file as executable, you know like every other executable file in linux.

Right click it, select permissions, check allow executing of file.

---

### Post by pytheas22 on 2010-06-09
> or you could just set the file as executable, you know like every other executable file in linux.

Right click it, select permissions, check allow executing of file. 

Of course, but that doesn't work if the file is on a CD, since then the file system is mounted read-only and you can't change permissions.  That's why I think this Executable Bit stuff is so poorly implemented (not to mention pedantic, since most people don't want a geeky lecture about Unix file permissions when they're trying to run files with wine).

---

### Post by jerome1232 on 2010-06-09
I agree, somethings needs to be adjusted for cd-rom's, so that it can still be used via normal gui methods.

But as for the geeky lectures about unix file-permissions, I'm going to say everyone could use a little more of it. (after all windows has been moving towards a more and more restrictive file permission system in vista and 7, so they will have to deal with it regardless )

---

### Post by g123386761 on 2012-05-22
> **pytheas22 said:**
> -snip-
You could also probably just edit the script at /usr/bin/cautious-launcher (which is what actually gets called when you try to open .exe files) to prevent it from doing anything, but I haven't tried that yet.
it works :O Thanks :D

---

### Post by oldos2er on 2012-05-22
Old thread closed.

---

