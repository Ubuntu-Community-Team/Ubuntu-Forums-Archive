---
title: "Trash Crash - Jaunty"
date: 2009-07-12
forum: General Help
---

### Post by Tman5293 on 2009-07-12
My computer goes into a complete freeze after emptying the trash. This has happened 3 times. 

SOMEONE HELP!!!!!!!!

---

### Post by chriskin on 2009-07-12
can you tell us anything else?

(might you be using ubuntuone?)

---

### Post by Tman5293 on 2009-07-12
I'm using Ubuntu 9.04 Jaunty

---

### Post by chriskin on 2009-07-12
i have no doubt about you using jaunty, but are you using ubuntu one?

it seems that it causes many problems like that, if not, let's wait for someone else to find a solution.

i don't know the command to empty it from the terminal, it would by worth it to try itfrom there

---

### Post by Tman5293 on 2009-07-12
im not using ubuntu one

---

### Post by deepkick on 2009-07-14
I have (had) the same problem. Some other posts say it can occur when emptying Trash when it contains large files, or a large amount of files. I beg to differ. I had my system lock up when deleting one or two files at a time. From what I gather, it may be an ext4 issue. Are you using ext4?

In any case, use the following to manually empty Trash from the terminal.

> sudo rm -r ~/.local/share/Trash/*

Haven't had any problems deleting some test files since then.

---

### Post by Johnny B on 2009-07-14
i think its a bug in ext4
im using ext3 until karmic

---

