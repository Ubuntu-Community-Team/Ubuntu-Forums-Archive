---
title: "firefox problems"
date: 2010-02-12
forum: General Help
---

### Post by urd on 2010-02-12
hi!, yesterday y try to update my firefox to firefox 3.6 using a guide of the forum, i do it, but since that my firefox doesn't work correctly ... i try to open a video on youtube and nothing happens what happened?? what can i do??

thanks for every help!!

pd: i have karmic

---

### Post by jken146 on 2010-02-12
Try this:
```

sudo apt-get purge flashplugin* && sudo apt-get install flashplugin-installer

```

---

### Post by urd on 2010-02-12
nope, nothing change :(

---

### Post by Enigmapond on 2010-02-12
What I did was to search for all the copies of the flash player, libflashplayer.so, and delete them. Then went to the adobe site, got it directly from them, made a folder .firefox in my home directory and made a folder in that 'plugins' and put the flash player right in there. Haven't had a problem since.

---

### Post by lovinglinux on 2010-02-12
> **urd said:**
> hi!, yesterday y try to update my firefox to firefox 3.6 using a guide of the forum, i do it, but since that my firefox doesn't work correctly ... i try to open a video on youtube and nothing happens what happened?? what can i do??

thanks for every help!!

pd: i have karmic

How did you install Firefox 3.6?

Your Ubuntu is 32bit or 64bit?

---

### Post by colobix on 2010-02-12
First of all, you shouldn't install the programs before they have been tested by ubuntu and are ready in the update box.
I don't know why you updated it but I can't see a reason as long as it worked fine before.
Anyhow, you should install the nonfree flash player, you can find it in synaptic.

---

### Post by urd on 2010-02-12
> **lovinglinux said:**
> How did you install Firefox 3.6?

Your Ubuntu is 32bit or 64bit?

i install it following the guide of the forum, for 32 bits, i try unistalling firefox, and erasing the repository that they wive there, and reinstalling from the original repositories and nothing happenes, still i cant see anything o youtube


this guide
[http://ubuntuforums.org/showthread.php?t=1352580](http://ubuntuforums.org/showthread.php?t=1352580)

---

### Post by lovinglinux on 2010-02-12
> **urd said:**
> i install it following the guide of the forum, for 32 bits, i try unistalling firefox, and erasing the repository that they wive there, and reinstalling from the original repositories and nothing happenes, still i cant see anything o youtube


this guide
[http://ubuntuforums.org/showthread.php?t=1352580](http://ubuntuforums.org/showthread.php?t=1352580)

Follow [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

---

### Post by urd on 2010-02-12
> **lovinglinux said:**
> Follow [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

man thanks, but nothing happens, still i can't see anything on youtube :(

---

### Post by lovinglinux on 2010-02-12
> **urd said:**
> man thanks, but nothing happens, still i can't see anything on youtube :(

Did you restart Firefox?

---

### Post by urd on 2010-02-12
> **lovinglinux said:**
> Did you restart Firefox?


daaaa ... i forget to do that... man thanks really ... finally works again

---

### Post by lovinglinux on 2010-02-12
> **urd said:**
> daaaa ... i forget to do that... man thanks really ... finally works again

You are welcome.

---

