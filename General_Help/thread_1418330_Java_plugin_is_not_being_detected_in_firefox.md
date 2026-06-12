---
title: "Java plugin is not being detected in firefox"
date: 2010-02-28
forum: General Help
---

### Post by chaanakya_chiraag on 2010-02-28
I have Ubuntu Karmic x32 and the Firefox version from the Mozilla Launchpad ppa, and Firefox isn't detecting the java plugin at all.  As in, it's not even being listed in the plugins manager.  What should I do?  If I need to give any more details about my system, please let me know.

---

### Post by scouser73 on 2010-02-28
For installing the 32 & 64 bit version of Java please follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by thecliff on 2010-02-28
Type "about: plugins" w/o a space in FireFox to see if one is already installed.  If so, try removing it and then using the instructions in the link above to reinstall.

---

### Post by chaanakya_chiraag on 2010-02-28
The problem is that, no matter how many times I reinstall the plugin, it's not appearing in about: plugins (w/o space)

---

### Post by mechro on 2010-02-28
Possibly a silly suggestion but have you ticked **Enable Java** in **Edit > Preferences > Content**?

---

### Post by chaanakya_chiraag on 2010-02-28
That's the thing: I can't find an "Enable Java" thing.  Although there **is** a Enable Javascript, although they aren't the same.

---

### Post by mechro on 2010-02-28
Each time you reinstall java are you removing the previous installation?

Also the fact that you're using "Firefox version from the Mozilla Launchpad ppa" may have something to do with it. Is there some reason you're not using the version available from the regular Ubuntu repositories?

---

### Post by chaanakya_chiraag on 2010-03-01
I only have one official Java plugin version installed (although I do have the openjdk I think, although I don't exactly know why).  For instance, I only have sun-java6-plugin installed right now.  I think you're right about the mozilla PPA thing.  As for why I'm using it: I just don't really want to wait for Lucid to get Firefox 3.6 :D

---

### Post by wojox on 2010-03-01
I've run both the Firefox nightly builds and stable from the ppa's and followed those instructions from scouser73 link and have it running.

You may want to double check everything.

---

### Post by chaanakya_chiraag on 2010-03-01
OK. I think I'll try to install the JDK manually (I need the jdk for some stuff). I just didn't wan to resort to that because I like repos over manual installation.

---

### Post by chaanakya_chiraag on 2010-03-03
scouser73: you are a lifesaver!  This worked!!!  Thank you all :)  I will now mark this thread as solved :)
- Chiraag

---

