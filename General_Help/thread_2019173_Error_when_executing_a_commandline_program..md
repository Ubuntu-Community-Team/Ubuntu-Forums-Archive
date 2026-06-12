---
title: "Error when executing a commandline program."
date: 2012-07-07
forum: General Help
---

### Post by Beatsleigher on 2012-07-07
Hey guys!

Every time I try to execute (e.g.) ADB (Android Debugging Bridge), I get following error:
[ATTACH]220816[/ATTACH]

It's saying something about a lib., but everything is installed, as it worked on my installation of 11.10... Kann someone help me, please?

---

### Post by steeldriver on 2012-07-07
are you on a 64-bit platform? a quick google suggests it's because the 64-bit version is looking for 32-bit libs (which won't be present on a 64-bit installation by default)

[http://stackoverflow.com/questions/10005907/eclipse-android-plugin-libncurses-so-5](http://stackoverflow.com/questions/10005907/eclipse-android-plugin-libncurses-so-5)

HTH

---

