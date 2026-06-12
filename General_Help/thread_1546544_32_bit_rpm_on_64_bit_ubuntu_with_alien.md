---
title: "32 bit rpm on 64 bit ubuntu with alien?"
date: 2010-08-05
forum: General Help
---

### Post by lykwydchykyn on 2010-08-05
I got a new computer at work this week.  I'm determined to get switched to 64 bit this time around, but what held me up last time was getting my email client to work.

We use Novell Groupwise 7, which is available as a 32bit rpm.  alien installed it fine in 32 bit Ubuntu, but when I try the same in 64-bit I get this error:
```

dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

```

How do I get this installed?

---

### Post by sydbat on 2010-08-05
> **lykwydchykyn said:**
> I got a new computer at work this week.  I'm determined to get switched to 64 bit this time around, but what held me up last time was getting my email client to work.

We use Novell Groupwise 7, which is available as a 32bit rpm.  alien installed it fine in 32 bit Ubuntu, but when I try the same in 64-bit I get this error:
```

dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

```

How do I get this installed?Not sure. You might be boned...unless Novell has a 64bit version.

This might help?? - [http://www.start64.com/index.php?option=com_content&task=view&id=1878&Itemid=70](http://www.start64.com/index.php?option=com_content&task=view&id=1878&Itemid=70)

---

### Post by lykwydchykyn on 2010-08-05
I'll check out the link.  I managed to generate an amd64 .deb file by extracting the rpm using "alien -g" and editing the debian/control file, then running the debian/rules file.

The deb installs fine, and the program tries to run when I run it.

Now... here's the hitch.

groupwise requires libstdc++5.  This is no longer in the lucid repos.  I can install the version for Karmic, but it installs the 64 bit libs.  I need to install the 32 bit libs.

Anyone know how to do this?

---

### Post by sydbat on 2010-08-05
> **lykwydchykyn said:**
> I'll check out the link.  I managed to generate an amd64 .deb file by extracting the rpm using "alien -g" and editing the debian/control file, then running the debian/rules file.

The deb installs fine, and the program tries to run when I run it.

Now... here's the hitch.

groupwise requires libstdc++5.  This is no longer in the lucid repos.  I can install the version for Karmic, but it installs the 64 bit libs.  I need to install the 32 bit libs.

Anyone know how to do this?This?? - [http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html](http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html)

---

### Post by lykwydchykyn on 2010-08-06
Well, I got libstdc++5 installed from an old copy of ia32libs.

Now the hurdle is that the built-in jre is broken, and using the system one isn't working...

Maybe I should stick to 32 bit pae.

---

### Post by kr651129 on 2010-08-06
Can I ask why you want to go 64?  I got my machine over to 64 but I keep having to many little problems to justify it flash, audio, weird video problems etc etc

---

### Post by lykwydchykyn on 2010-08-06
Yay!  it's working.  I did all the steps in that first link you posted (with some modifications to get the newest packages possible) and it works now.

Now... the rest of the hurdles...

---

