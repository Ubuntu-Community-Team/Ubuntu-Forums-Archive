---
title: "Getting flash to work in chromium"
date: 2010-07-23
forum: General Help
---

### Post by COKEDUDE on 2010-07-23
[http://blog.chenhow.net/2009/07/13/internet/install-chromium-flash-plugin-in-ubuntu-jaunty/](http://blog.chenhow.net/2009/07/13/internet/install-chromium-flash-plugin-in-ubuntu-jaunty/)

Please look at part 4. 
chenhow@chenhow-laptop:~$ cd /usr/lib/chromium-browser/plugins
chenhow@chenhow-laptop:/usr/lib/chromium-browser/plugins$ sudo ln -s ../../adobe-flashplugin/libflashplayer.so
chenhow@chenhow-laptop:/usr/lib/chromium-browser/plugins$ sudo vim /etc/chromium-browser/default
### Edit chromium flags in default file ###
# Options to pass to chromium-browser
CHROMIUM_FLAGS=”–enable-plugins”

Is there any point of adding the –enable-plugins? Plugins are already enabled when I check the about: plugins.

---

### Post by kerry_s on 2010-07-23
dude, chromium-browser is already in the repo, just open synaptic & install it. for all the restricted stuff including flash, install "ubuntu-restricted-extras".

that how to is outdated, you don't need to do any of that.

---

### Post by watupgroupie on 2010-07-23
Not to mention you have like three threads all dealing with Chromium now I think.

---

### Post by COKEDUDE on 2010-07-23
> **watupgroupie said:**
> Not to mention you have like three threads all dealing with Chromium now I think.

Its not working for me so I am trying several different methods :P.

---

### Post by watupgroupie on 2010-07-23
What exactly is not working for you?

---

### Post by COKEDUDE on 2010-07-30
> **watupgroupie said:**
> What exactly is not working for you?

Getting flash to work in chromium like my title says.

---

### Post by gordintoronto on 2010-07-30
Did you install the restricted extras?

---

### Post by COKEDUDE on 2010-07-31
I tried all of them, and then I tried one at a time. Neither of those worked for me.

---

