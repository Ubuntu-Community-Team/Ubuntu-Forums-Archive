---
title: "Remove firefox without removing java plugin?"
date: 2010-06-05
forum: General Help
---

### Post by josephellengar on 2010-06-05
Hi.  I'm on 9.10 x64 gnome.  I hate firefox and want to remove it because I use chrome, but when I try to remove it it removes the java plugin.  And when I try to install the java plugin alone, it installs firefox.  Why are these dependencies of each other?  That doesn't make sense.  Is there any way that I can remove ff without removing java?

---

### Post by Ron S on 2010-06-05
Hi try this link [http://ubuntuforums.org/showthread.php?t=1255646](http://ubuntuforums.org/showthread.php?t=1255646) hope it helps.

---

### Post by josephellengar on 2010-06-05
> **Ron S said:**
> Hi try this link [http://ubuntuforums.org/showthread.php?t=1255646](http://ubuntuforums.org/showthread.php?t=1255646) hope it helps.

I have java installed, I just want to be able to uninstall firefox.  For some reason they're considered dependencies.

---

### Post by Ron S on 2010-06-05
Do you have the sun java plugin installed. I think you need to enable the Medibuntu repository and then install the sun-java6-plugin which is supposed to support Mozilla and other browsers without showing firefox as a dependency .

---

### Post by josephellengar on 2010-06-05
> **Ron S said:**
> Do you have the sun java plugin installed. I think you need to enable the Medibuntu repository and then install the sun-java6-plugin which is supposed to support Mozilla and other browsers without showing firefox as a dependency .

I did enable the repository and have the sun-java6 plugin installed.  When I try to remove firefox it says that it also has to remove the plugin.

---

### Post by mkvnmtr on 2010-06-05
I thought Chrome comes with its own flash. Does it disable Chrome flash when you remove Firefox?

---

### Post by josephellengar on 2010-06-06
> **mkvnmtr said:**
> I thought Chrome comes with its own flash. Does it disable Chrome flash when you remove Firefox?

I'm not talking about flash.  I'm talking about java.  But no.  The flash installer is not dependent on flash or vice versa.

---

### Post by josephellengar on 2010-06-12
I still can't figure this out.  Every time I try to remove firefox it removes java.  And every time I try to install java without firefox it also installs firefox.  Is there any way that I can uninstall firefox with some sort of --ignore-dependencies flag or something?  Would this destroy my package management?  I just use chrome and this is so annoying.  It's not even happening on my netbook-only on my workstation.  It's 64-bit, which might be a difference.

---

