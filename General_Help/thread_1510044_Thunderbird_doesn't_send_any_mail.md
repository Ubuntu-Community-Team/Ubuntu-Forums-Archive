---
title: "Thunderbird doesn't send any mail"
date: 2010-06-15
forum: General Help
---

### Post by Achilles124 on 2010-06-15
I can receive mail with Thunderbird. Just cannot send it. 

Running Thunderbird in the terminal results in the following error:

> ecmpeek@ecmpeek-desktop:~$ LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so [libxul.so: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so [libxul.so: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet]
deliver mode: 0

What can be done?

---

### Post by Achilles124 on 2010-06-16
nobody?

---

### Post by philinux on 2010-06-16
[https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/570594](https://bugs.launchpad.net/ubuntu/+source/lightning-sunbird/+bug/570594)

---

### Post by Linux_junkie on 2010-06-16
It sounds like connection to smtp server has not been set up correctly.  Check this option in Thunderbird.

---

### Post by Achilles124 on 2010-06-16
What do you think it is? wrong smtp or wrong Icedtea?

It sound like it is a case of the chicken and the egg.

---

### Post by philinux on 2010-06-16
> **Achilles124 said:**
> What do you think it is? wrong smtp or wrong Icedtea?

It sound like it is a case of the chicken and the egg.

Disable the lightning plugin and see if you're good.

---

### Post by Achilles124 on 2010-06-17
that is weird, my home folder has two thunderbird folders with exactly the same content.

~/.thunderbird
~/.mozilla-thunderbird

I cannot find the icedtea plugin in thunderbird. It is not in the addon folder.

---

