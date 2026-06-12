---
title: "Where are the flash files?!!"
date: 2011-05-24
forum: General Help
---

### Post by ohsnap59 on 2011-05-24
Does anyone know where the tmp/flash files are located in 11.04? I don't want to download the Youtube downloader or whatever it is at this point. The files should be somewhere!

---

### Post by linuxinstalledfromhdd on 2011-05-24
They don't want you doing that. Adobe Flash has changed the way it works. So has Firefox. 

You need to install Flash plugin 9, the old old old ancient one now, and the files will magically show up again in your /tmp directory 

You can download the obsolete compressed file for that plugin in your home directory, and then you can install Flash-Aid plugin to help you install it.

---

### Post by nothingspecial on 2011-05-25
They are stored in your ram. To find them type this
```

f="$(ls -l  /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```

The flv file is the number.

You are not supposed to copy them to your hard disk though.

---

### Post by JOHNNYG713 on 2011-05-25
netvideohunter in firefox add ons lets you download any video and save it where you like ! FYI :D

---

### Post by ohsnap59 on 2011-05-25
> **linuxinstalledfromhdd said:**
> They don't want you doing that. Adobe Flash has changed the way it works. So has Firefox. 

You need to install Flash plugin 9, the old old old ancient one now, and the files will magically show up again in your /tmp directory 

You can download the obsolete compressed file for that plugin in your home directory, and then you can install Flash-Aid plugin to help you install it.
Will there be incompatibility issues if I do that?

---

### Post by ohsnap59 on 2011-05-25
> **JOHNNYG713 said:**
> netvideohunter in firefox add ons lets you download any video and save it where you like ! FYI :D
Thanks

---

### Post by uRock on 2011-05-25
Downloading from Youtube is against their ToS.

Thread Closed.

---

