---
title: "Minecraft Black Screen"
date: 2010-11-28
forum: General Help
---

### Post by Veector on 2010-11-28
Im using Ubuntu 10.10, chromium and when i go to play minecraft in thir website it just shows a black screen.
WHan can i do to make this work?

---

### Post by HPD2 on 2010-11-28
Install sun java not open java. Thats how I was able to get minecraft working.

---

### Post by Locke_99GS on 2010-11-28
After you've installed the Sun stuff, make sure to tell the system that you want to use Sun's Java.
```

sudo update-java-alternatives -s java-6-sun

```
Restart the browser.

If you still have issues, try removing the IcedTea and OpenJDK stuff.

---

### Post by Veector on 2010-11-28
I tried installing sun java by downloading the 64bit version from their website and then installing it as root  [./jre-6u22-linux-x64\ \(1\).bin ] i put the command sudo update-java-alternatives -s java-6-sun and i got this back

update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for pluginappletviewer.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
and mine craft still does not work =/
what else can i do?

---

### Post by Locke_99GS on 2010-11-28
Install it from the repo's - it will place things in their proper locations.
```

sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
sudo update-java-alternatives -l

```
After installing Java, the last command should list a couple possible Java installations. Choose the Sun java.
```

sudo update-java-alternatives -s java-6-sun

```

Restart browser, and try Minecraft.

If Minecraft won't play now, try removing IcedTea and OpenJDK.

```

sudo apt-get remove --purge icedtea* openjdk*

```

Then set the java alternative to Sun again, restart browser again, and try Minecraft again.

---

### Post by Veector on 2010-11-28
I got it working, thanks!:p

---

