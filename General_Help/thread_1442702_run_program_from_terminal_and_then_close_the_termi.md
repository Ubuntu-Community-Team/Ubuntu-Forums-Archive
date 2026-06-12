---
title: "run program from terminal and then close the terminal"
date: 2010-03-30
forum: General Help
---

### Post by xandout on 2010-03-30
Hey all i have a seemingly simple desire but i cant get it right.
my .xinitrc is as follows

...
...
...
openbox
sleep 5
xfce4-panel



since that only starts openbox 

i would like to know how to get it to also start the xfce panel


any help would be appreciated


also how can i run say firefox from a term and be able to close that term window without killig FF?

---

### Post by falconindy on 2010-03-30
Your xinitrc should **end** with launching openbox.
```
...
xfce4-panel&
exec /usr/bin/openbox
```

If you want to be able to close a terminal you launched a process from, you need to disown the process from job control:
```
$ firefox&
$ disown
```

---

### Post by xandout on 2010-03-30
Thank You So MUCH.  Ubuntu users are awsome!!!!!!!!!!

---

