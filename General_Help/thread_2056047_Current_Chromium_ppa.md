---
title: "Current Chromium ppa"
date: 2012-09-10
forum: General Help
---

### Post by blazoner on 2012-09-10
I am using this post as a note-to-self, if it helps you, even better.

The Chromium-Browser available through the repositories is unfortunately very outdated. Fortunately there is a simple fix.

Taken from this [post]("http://handytutorial.com/install-latest-chromium-browser-in-ubuntu/").

Install Chromium browser:
Update: ppa:a-v-shkop/chromium-dev will try to maintain more-or-less fresh releases of Chromium while Chromium Team won’t release new versions of Chromium browser. Install from this ppa (for now only support Ubuntu 12.04):

```
sudo add-apt-repository ppa:a-v-shkop/chromium-dev
sudo apt-get update
sudo apt-get install chromium-browser
```

The OP gives a non-install version as well, but the ppa is working well for me, and it is a simple fix.
I am now running Version 23.0.1246.0 Ubuntu 12.04 (153452) sweet as you please. 8-)

***NOTE*** You do not need to re-install chromium-browser, but re-installing won't hurt. It will update your current install through Update Manager automatically the next time it is run. Or you can just run update manager manually.

---

### Post by Epodx64 on 2012-09-10
Only problem is it's only for 32bit systems 64bit requires IA32 libs I just run 
Google Chrome Version 23.0.1255.0 dev 64bit it's the closest you can get to the chromium dev or daily builds for 64bit systems.

---

### Post by blazoner on 2012-09-11
Interesting, as I am running 12.04 64 bit myself with no problems.

---

### Post by blazoner on 2012-09-11
Come to think of it, I do have IA32 libs installed already so didn't notice the change... Just can't bring myself to use Chrome instead of Chromium....

---

### Post by tehk on 2012-09-11
> **Epodx64 said:**
> Only problem is it's only for 32bit systems 64bit requires IA32 libs I just run 
Google Chrome Version 23.0.1255.0 dev 64bit it's the closest you can get to the chromium dev or daily builds for 64bit systems.

WRONG!

Download daily builds of Chromium here:
[http://download-chromium.appspot.com/](http://download-chromium.appspot.com/)

---

### Post by AndyOpie150 on 2012-09-11
Thanks blazoner. Worked great.
 New to Ubuntu (dual booted because I wasn't sure), but I liiiike it! The support here is incredible as well.

---

