---
title: "install cd lost"
date: 2006-02-02
forum: General Help
---

### Post by dragonflyFZX on 2006-02-02
hi,

i am trying to follow this thread

[http://ubuntuforums.org/showthread.php?p=423589]("http://ubuntuforums.org/showthread.php?p=423589")

when executing this command:

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base

ubuntu prompts me to insert the install cd.  But, i lost it...  I could of course download the cd again and burn it, but i was wondering if i could not get the packages from the repositories?

my sources.list are adapted to what it sais it should be in the post.

---

### Post by g-a-c on 2006-02-02
Sounds to me like you've put the extra repositories in, but haven't commented out the line at the top for the CD (thus you have the CD and net both enabled). Apt is probably just assuming that if the packages are the same versions, you'd rather use the ones from the CD instead of wasting time downloading them. If you comment out the "deb cdrom" line at the top and do another apt-get update you should be able to do what you want.

---

### Post by frodon on 2006-02-02
It sounds like a small source.list problem, i think you didn't remove the line about the install CD. Post your source.list file here if you need help with this file.

---

### Post by az on 2006-02-02
[QUOTE=dragonflyFZX]hi,


my sources.list are adapted to what it sais it should be in the post.[/QUOTE]
Did you update?

sudo apt-get update

or refresh in synaptic?

---

### Post by dragonflyFZX on 2006-02-02
you are absolutely correct about not having commented out the cd line.  Thanks :p

---

