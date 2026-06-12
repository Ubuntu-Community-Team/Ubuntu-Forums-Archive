---
title: "udev[488] can't read file on boot. Should I care?"
date: 2010-01-11
forum: General Help
---

### Post by Rallg on 2010-01-11
In Ubuntu 910 on my Asus EEE-PC1005HA, I notice that during boot, when the screen is dark between the plain Ubuntu logo and the animated purple screen, there is a brief message:

udev[488] cannot read file (rest of message goes by too fast for me)

This doesn't seem to hurt anything. My system has been working just fine for a long time. I don't know how long the message has been there. Perhaps it merely lengthens boot time? Should I care? If I should care, where might the message be logged (so that I don't have to photograph the screen)?

---

### Post by warfacegod on 2010-01-11
If you don't notice anything bad happening then I wouldn't worry about it too much.

---

### Post by Rallg on 2010-01-11
The only "bad" thing (if anything) is that I believe boot is delayed while it looks for the missing file.

Maybe it reads this:

Cannot open file /etc/udev/rules.d/z80_user.rules

SOLVED: Finally I could read the error message, then locate the file. It had zero bytes, and apparently boot didn't like that. I wrote a comment into the file, and now there's no message on boot.

As warfacegod noted, it wasn't really a problem.

---

### Post by warfacegod on 2010-01-11
If it's been weeks doing this for weeks, it probably always did. If not and you don't care about 30 seconds extra boot time then ignore it. I just checked out your Warning and it looks like it has something to do with the splash screen. I found a patch for it but every place I read said don't do it. The potential to hose your system isn't worth the minor issue.

---

### Post by Rallg on 2010-01-11
Ignored, for sure. I have no idea how long it's been giving that message. But I recently made some changes, so maybe I was paying more attention.

---

### Post by dcstar on 2010-05-15
[http://ubuntuforums.org/showpost.php?p=9302412&postcount=5](http://ubuntuforums.org/showpost.php?p=9302412&postcount=5)

---

