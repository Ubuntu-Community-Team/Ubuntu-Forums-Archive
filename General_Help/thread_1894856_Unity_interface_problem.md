---
title: "Unity interface problem"
date: 2011-12-13
forum: General Help
---

### Post by NShekar on 2011-12-13
I installed compizconfig on my ubuntu 11.10 & started editing some options on it to suit my taste but suddenly it seemed like the system did not respond & I restarted the system & to my astonishment there is only a main menu bar on the top & no Unity desktop.
i don't know the reason behind this problem & would appreciate some help to solve this.

---

### Post by TeoBigusGeekus on 2011-12-13
Open a terminal and try
```
unity --reset
```

---

### Post by NShekar on 2011-12-13
I tried that code but it took very long to respond , I mean to say it never responded & since there is no option of shutting down the system had to manually restart the system.

---

### Post by TeoBigusGeekus on 2011-12-13
> **NShekar said:**
> I tried that code but it took very long to respond , I mean to say it never responded & since there is no option of shutting down the system had to manually restart the system.

Very bad idea...
Do it again and leave it for as long as it takes. If it takes more than 15minutes, open another terminal and give
```
sudo reboot
```
to restart your pc.

---

### Post by NShekar on 2011-12-13
I tried it once again but no results . This time I waited for 30 minutes & there was no noticeable changes so had to reboot the system.
Is there anything else that I can do so that I don't have to re-install.

---

### Post by stinkeye on 2011-12-13
Firstly make sure your in the "ubuntu" session.
```
echo $DESKTOP_SESSION
```

Try to reset compiz to defaults and re-enable the unity plugin.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```


Give it 30 secs or so to run and if it doesn't load properly, run
```
compiz --replace & disown
```

---

### Post by NShekar on 2011-12-14
all set & running same as before. 
thanks for the help.

Ubuntu one of the best!!

---

