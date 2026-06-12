---
title: "NEed help! hang upon boot up!"
date: 2011-02-13
forum: General Help
---

### Post by jinjin on 2011-02-13
ok so here is the story. i already have a hard drive dual booted with xp and ubuntu and it works perfectly.  i used easus partition to ghost this drive on to another drive.  the other drive worked perfectly to.  then i decided that i wanted to try to put mac osx86 on the second drive, it turned out there was some problem and i had to format it to GPT format but then i did some other stuff and that macosx86 was not going to work out. so in the end i used easus to make the drive an in MBR format again.  then i second drive using the info from the first drive again,  however, whereas before the second drive was still able to boot, this time when it boots, it does not load grub, it just hangs and says "grub _ "  on the top left and just does not.  what is wrong now?  how can i fix this? please help?

---

### Post by jinjin on 2011-02-14
ok  i solved it myself.  you have yo reinstall grub 2 using the live cd.


however, when do you reinstalll grub 2 and try to boot windows xp, you're going to get a "device not found error", in which case you must boot ubuntu, open terminal and do "update-grub"

---

