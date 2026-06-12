---
title: "Possible to install wubi other than c:\ubuntu?"
date: 2011-02-18
forum: General Help
---

### Post by janz84 on 2011-02-18
I'm wondering if there are some command line switches or something to allow wubi to install to a location other than c:\ubuntu. I need this because I have my system configured with an 80GB ssd and a 2TB data hd. I would prefer to put ubuntu on the data hd. If this is not possible, would the system bug out if I created a ntfs junction link to d:\ubuntu? I already use this technique to trick windows into thinking the \users\ and the \programdata\ folders are on the c:\ drive but actually reside on the d:\

Thanks,

janz84

---

### Post by bcbc on 2011-02-18
You can select a different 'drive' from the Installation Drive drop down box on the main Wubi setup screen. [https://wiki.ubuntu.com/WubiGuide#How do I install Ubuntu?]("https://wiki.ubuntu.com/WubiGuide#How do I install Ubuntu?")

Also read the [https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

---

### Post by janz84 on 2011-02-18
Thanks, I missed the first drop down there.

[QUOTE="https://wiki.ubuntu.com/WubiGuide#Warning"]These problems can be avoided on a fresh install by locking the grub-pc and grub-common packages[/QUOTE]

Also, this is a good thing to keep in mind.

---

