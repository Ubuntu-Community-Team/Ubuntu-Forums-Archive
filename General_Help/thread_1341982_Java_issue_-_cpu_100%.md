---
title: "Java issue - cpu 100%"
date: 2009-11-30
forum: General Help
---

### Post by zerek on 2009-11-30
Sun Java (JRE) 6
aoss javaws [http://files.gokgs.com/javaBin/cgoban.jnlp](http://files.gokgs.com/javaBin/cgoban.jnlp)

I've been using gokgs for quite some time now, worked perfectly until I upgraded ubuntu to 9.10

After a few minutes ingame, I lose all sound, starting to lag badly and cpu monitor goes berserk.
(usually got cpu 1&2 running at 10-15%, but when running cgoban.jnlp it ends up at cpu1:20%, cpu2: 100%)

I've tried to clear cache, 
sudo update-java-alternatives -s java-6-sun


Update:  It seems like its the alsa-oss that's causing the problem.
Still don't know how to fix it.

---

