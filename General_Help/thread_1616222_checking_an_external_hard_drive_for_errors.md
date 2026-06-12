---
title: "checking an external hard drive for errors"
date: 2010-11-07
forum: General Help
---

### Post by inspiteofmyself on 2010-11-07
i am currently running palimpsest (system -> administration -> disk utility) and letting it "check" an unmounted filesystem.

i know its just running fsck.ext3 on this drive... the drive is formatted ext3, and is used on a hardware media player (WDTV Live Plus) in another room... i just moved it in here to avoid copying recorded HD shows over the LAN.

anyway, i was informed at boot with this drive connected that it needed to be checked, after booting it is mounted, but says it has errors and needs to be checked. it is checking, i would assume messages from fsck.ext3 would be logged to /var/log/fsck/checkfs, but i have never been interested in this type of thing before... usually when my drives start to get errors, its time to replace them... this one im sure is caused by being unmounted incorrectly by the stupid WDTV Live Plus...it locks up sometimes, lol...

i dunno, this is a big drive. just wish there was some "status update" other than a whirling indicator... im tailing the log file i mentioned above, but so far it just has "Nothing has been logged yet." (which i take as a really good thing at this point. lol.

EDIT: at the very end of the filesystem check, i got a message about the filesystem being clean with no errors. id still like more of an indication than "whirling indicator thingy"...guess ill go back to CLI for checking filesystems. lol

---

### Post by bioterror on 2010-11-07
This is easy like a monday morning.

In Terminal:
```
df -h
sudo umount /dev/sdX (you'll see the letter for that from df -command)
sudo fsck.ext3 /dev/sdX
sudo mount /dev/sdX /media/YourMount/Point or disconnect and plug it back :D
```

---

### Post by inspiteofmyself on 2010-11-08
> **bioterror said:**
> This is easy like a monday morning.

In Terminal:
```
df -h
sudo umount /dev/sdX (you'll see the letter for that from df -command)
sudo fsck.ext3 /dev/sdX
sudo mount /dev/sdX /media/YourMount/Point or disconnect and plug it back :D
```

oh i know how to check a filesystem already. i just wanted to know if there was some way to monitor what was going on behind palimpsest when you tell it to check a filesystem. the little whirly thingy was driving me insane, and i had no idea what (or if) it was doing anything.

---

### Post by bioterror on 2010-11-08
> **inspiteofmyself said:**
> oh i know how to check a filesystem already. i just wanted to know if there was some way to monitor what was going on behind palimpsest when you tell it to check a filesystem. the little whirly thingy was driving me insane, and i had no idea what (or if) it was doing anything.

Ahh...
```
fsck -v
``` should tell you what's happening as it's verbose.

---

