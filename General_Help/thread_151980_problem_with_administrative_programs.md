---
title: "problem with administrative programs"
date: 2006-03-28
forum: General Help
---

### Post by slipk487 on 2006-03-28
i can not open ant thing in the administrative porgrams list or the add programs thing so what counl be wrong

---

### Post by aysiu on 2006-03-28
Go to Applications > Accessories > Terminal and type ```
gksudo synaptic
``` and post here (copy and paste) the exact output.

---

### Post by slipk487 on 2006-03-28
nothing came up

---

### Post by aysiu on 2006-03-28
[QUOTE=slipk487]nothing came up[/QUOTE] "Nothing" as in: ```
slipk487@ubuntu:~$ gksudo synaptic
slipk487@ubuntu:~$
``` Is that what happened? If not, can you post exactly what "nothing" was?

---

### Post by slipk487 on 2006-03-29
that is wat it did so what does that mean

---

### Post by aysiu on 2006-03-29
[QUOTE=slipk487]that is wat it did so what does that mean[/QUOTE] It means something's seriously wrong, and unfortunately I don't know how to fix it.

Apparently, though, [you're not alone](http://www.ubuntuforums.org/showthread.php?t=151149).

---

### Post by trent dillman on 2006-03-29
Try this in a terminal:
```

sudo apt-get install --reinstall gksudo

```

---

### Post by aysiu on 2006-03-29
Just for the record, it should probably be something like this: ```
slipk487@ubuntu:~$ groups
slipk487 adm dialout cdrom floppy audio dip video plugdev users lpadmin scanner admin
```

**Edit**: Apparently trent deleted the command *groups*...?

---

### Post by trent dillman on 2006-03-29
Yeah, I realized that sudo was probably working, just not gksudo.

Sorry.

---

### Post by slipk487 on 2006-03-29
slipk487@slipk487:~$ sudo apt-get install --reinstall gksudo
Password:
slipk487@slipk487:~$ sudo apt-get install --reinstall gksudo
Password:



i tryed it twice and that is what came up

---

### Post by slipk487 on 2006-03-30
i finally got it fixed i had to reinstall it but i still cant figure out how to use my radeon graphics card i had to reinstall it twice because it wouldnt but up the GUI it froze or something right before the GUI screen comes up

---

