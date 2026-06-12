---
title: "Destroyed GNOME/X trying to install XGL (noob)"
date: 2006-04-06
forum: General Help
---

### Post by Demonfire on 2006-04-06
I tried to install XGL on breezy badger, which sorta didnt work


Yeah, i know it was a stupid idea, and now im locked out of graphical mode......


Im stuck to only using command line, which is sorta problematic seeing as im sorta inexperienced in the realm of that stuff. Is there some command i can use to rebulid X and GNOME to get stuff running up to speed again?

Thanks.

---

### Post by tseliot on 2006-04-06
Which guide did you use? (post the link)

Maybe you didn't destroy gnome.


EDIT: Try this command:
```
[COLOR="Red"]sudo rm /etc/gdm/gdm.conf-custom[/COLOR]
```

---

### Post by Demonfire on 2006-04-06
[http://www.ubuntuforums.org/showthread.php?t=133772&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=133772&highlight=xgl)

Im sure i didnt "destroy" gnome, i just made it unusable so whenever i try to get into it i get that xserver error with the codes that are supposed to help you.

---

### Post by testube_babies on 2006-04-07
i'm sure if you post some of the error codes, someone around here will be able to help you.  i ran into the same problem last week, it turned out that i had an extra character in my xorg.conf file that caused x to crash upon loading.

---

### Post by testube_babies on 2006-04-07
also, (sorry for double posting), with that particular tutorial you could try:

cd /etc/gdm
sudo mv gdm.conf gdm.conf.old
sudo mv gdm.conf.backup gdm.conf

this backs up your "bad" configuration file (just in case, i have no idea why you would ever need it but who knows).  then, it restores the backup you made while doing the tutorial.

---

### Post by Demonfire on 2006-04-07
thanks, ill try it out

---

### Post by Demonfire on 2006-04-07
Hey, thanks for the help. It worked completely, i just had to reinstall the drivers.

I still have one problem though, videos will not run. And when i go to the multimedia systems selector to select a video source and test them, none of the tests pass.

any ideas?

---

