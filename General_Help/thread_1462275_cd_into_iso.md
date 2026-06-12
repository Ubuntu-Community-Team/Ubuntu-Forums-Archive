---
title: "cd into iso"
date: 2010-04-25
forum: General Help
---

### Post by sxmaxchine on 2010-04-25
Hello i just wanted to know how i can make an iso from the files on a cd.

---

### Post by KeyserSoze93 on 2010-04-25
To make ISO from CD in drive:

```

dd if=/dev/cdrom of=my_cd.iso

```

To write it back to the CD:

```

wodim -v -eject -speed=16 my_cd.iso

```

---

### Post by elliotn on 2010-04-25
u can us brasero than using this confusing commands

---

### Post by sxmaxchine on 2010-04-25
Thankyou for the answers i'l try braeso however i will also remember that command because i like to know commands that do things.

---

### Post by KeyserSoze93 on 2010-04-25
> **elliotn said:**
> u can us brasero than using this confusing commands

What's confusing about those commands? dd is a data dump command, /dev/cdrom is the CD drive and my_cd.iso is the name of the ISO.

Wodim is Write Optical DIsc Media, -speed=16 is the write speed, -eject means eject the disc after writing and -v means report the status as the disc is being written.

Less confusing, in my opinion, than a GUI. After all, if the user was running Kubuntu, then k3b would be the program to use. Some versions, I believe, use Gnome Baker.

With these two commands, it doesn't matter what desktop and other software is present on the system.

---

### Post by sxmaxchine on 2010-04-26
i found the code to be quicker then opening a program and clicking all the buttons.

---

