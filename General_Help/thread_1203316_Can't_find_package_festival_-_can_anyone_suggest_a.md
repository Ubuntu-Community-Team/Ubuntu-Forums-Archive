---
title: "Can't find package festival - can anyone suggest a repo?"
date: 2009-07-03
forum: General Help
---

### Post by mrming on 2009-07-03
I'm trying to install festival tts in Ubuntu Jaunty but the package isn't there. I'm using the sources.list from [this thread]("http://ubuntuforums.org/showthread.php?t=1157181"). Can anyone suggest a repo I might get it from? I used to be able to see the package when I was using Hardy, but since I installed Jaunty, it's gone.

---

### Post by coffeecat on 2009-07-03
Do you mean Festival, the text to speech app? I presume tts is text to speech. A 1.96~beta version is in the Jaunty Universe repository. If you can't find it in Synaptic, make sure you have the Universe repo enabled.

---

### Post by sisco311 on 2009-07-03
festival is in the univers repos:
```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install festival
```

---

### Post by mrming on 2009-07-03
You guys are legends - thanks so much!

---

