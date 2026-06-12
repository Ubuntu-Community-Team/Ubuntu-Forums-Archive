---
title: "gdm-2.20 package killed my display!"
date: 2010-02-03
forum: General Help
---

### Post by squareff255 on 2010-02-03
So, I wanted to change the look of my login screen, so I installed  gdm-2.20 thru the terminal (apt-get install) and then it asked me what I  wanted the default set as and gave me 2 choices:
gdm
gdm-2.20
So,  I picked the latter. Then I restarted the compy and... text. It keeps  telling me that the X server is... not configured correctly and that I  need to restart GDM when it is. So, I need to know if there is any way  of rewriting the xorg.conf to work with my poc (piece of crap) video  card. I have a backup of the default xorg.conf for use with NO video  card... but then I wouldn't be able to use my video card... :)

---

### Post by squareff255 on 2010-02-13
lol I fixed it. I just went:
```

$ sudo apt-get install gmd

```
and then it reinstalled and asked if I'd rather use "gmd" or "gmd-2.20" as my default. Needless to say, I chose gmd. 
:) Cheers

---

