---
title: "How to delete partitions?"
date: 2009-08-22
forum: General Help
---

### Post by HolyMythos on 2009-08-22
I installed Ubuntu today, only to run out of diskspace since I didn't give enough space to Ubuntu. I was told that instead of using gparted that I could just install ubuntu again. I did, thinking it would delete my old Ubuntu, but now it gave me another partition. So, I have vista, ubuntu, and another ubuntu. Problem is, even though I gave even more space to the second Ubuntu, I ran out of space AGAIN. I plan on getting rid of the old Ubuntu's and putting more space on, but I don't know how to do it.

How can I get rid of my old partitions (other than Vista)?

EDIT: I found a guide on how to do it, but I'm not sure which partitions Ubuntu uses. Here's a screenshot of my Disk Management window for my Computer. Which Volumes does Ubuntu use? All of the unnamed volumes? And if I delete them, when I startup my computer, will Vista be automatically selected to start up or will I get error messages since Ubuntu was my main OS?

[IMG]http://img12.imageshack.us/img12/3434/ubuntuproblems1.png[/IMG]

---

### Post by earthpigg on 2009-08-22
hi,

lesson learned: dont ever try to use windows tools to do anything involving linux. linux plays nice with windows, but not vice versa. :D

boot from a live cd, and run 'sudo gparted'.

let us know if looking at gparted from an Ubuntu LiveCD doesn't clear everything up for ya.

---

### Post by HolyMythos on 2009-08-22
> **earthpigg said:**
> hi,

lesson learned: dont ever try to use windows tools to do anything involving linux. linux plays nice with windows, but not vice versa. :D

boot from a live cd, and run 'sudo gparted'.

let us know if gparted from an Ubuntu LiveCD doesn't clear everything up for ya.

Alright, I did what you said and ran sudo gparted, now I'm at a loss at what to do. What I'm basically worried about is if I do delete my Ubuntu partitions, will my computer not work the next time I start up? Ubuntu is used as my normal startup OS, so if I delete it, what will happen?

---

### Post by earthpigg on 2009-08-22
the ubuntu install you did most *_recently_* is the only crucial one.

when you install ubuntu, it takes over the master boot record from whatever had it before -- another linux distro, another version of ubuntu, windows, it does not matter.

so, whichever you installed _*last*_ is the one you do _*not*_ want to wipe.

---

### Post by kjohri on 2009-08-22
Since your current Ubuntu partition is not big enough, you can delete both Ubuntu partitions and re-install Ubuntu. You need to do manual partitioning. So you can re-install Ubuntu and opt for manual partitioning during install. During this manual partitioning, you can delete all the previous Ubuntu partitions and make a new one for this install.

---

### Post by HolyMythos on 2009-08-22
> **kjohri said:**
> Since your current Ubuntu partition is not big enough, you can delete both Ubuntu partitions and re-install Ubuntu. You need to do manual partitioning. So you can re-install Ubuntu and opt for manual partitioning during install. During this manual partitioning, you can delete all the previous Ubuntu partitions and make a new one for this install.

If I do this, will it still make the Ubuntu I'm installing the main boot OS? If so, this is exactly what I want to do, and you're my jesus.

---

### Post by earthpigg on 2009-08-22
> **HolyMythos said:**
> If I do this, will it still make the Ubuntu I'm installing the main boot OS? If so, this is exactly what I want to do, and you're my jesus.

this is correct.

note, however, that between the time of deleting the existing ubuntu partitions and reinstalling, you will not be able to boot into windows.

---

