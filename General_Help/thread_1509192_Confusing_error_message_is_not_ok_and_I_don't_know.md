---
title: "Confusing error message is not ok and I don't know how to fix it!"
date: 2010-06-13
forum: General Help
---

### Post by LordMelvin on 2010-06-13
Hi, everyone.

After two+ years of ubuntuing (and nounverbing) I've finally run across an error I can't figure out on my own.

```
username@redacted:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package katalog is not ok and I don't know how to fix it!

```

an identical error appears on every other apt-anything I've tried to do, or on opening Synaptic. The place where this gets weird is that not only do I not have the app 'Katalog' installed, I'm running a near-vanilla two-day old gnome install, and shouldn't have any of those irritating kde-spelled packages hanging around...
Any thoughts? Suggestions?

---

### Post by rukiaEnix on 2010-06-13
try this:

```

$ ln -sf /bin/true /var/lib/dpkg/info/katalog.postrm 

```

---

### Post by LordMelvin on 2010-06-14
same error from console with or without the symlink

Synaptic is throwing a two-line error message, as follows:

```
E: The package katalog is not ok and I don't know how to fix it!
E: Internal error opening cache (1). Please report.

```

---

### Post by rukiaEnix on 2010-06-14
go to this thread they have already solve it :p

[http://ohioloco.ubuntuforums.org/showthread.php?p=5602022](http://ohioloco.ubuntuforums.org/showthread.php?p=5602022)

---

### Post by LordMelvin on 2010-06-14
hurrah! your Google-fu is most powerful! Many thanks!

---

### Post by rukiaEnix on 2010-06-14
haha you just have to use the right words XD. now you can say this thread is solved :p

---

