---
title: "black screen/ need help"
date: 2009-11-30
forum: General Help
---

### Post by Alromaiky on 2009-11-30
hallo every one 
first of all, i don't know if this in the right place or not, 
so if that a mistake then i'm so sorry. 

i have a problem with a black screen on my Karmik Kuala launch every 10  min. 
however my screen saver is not a black screen and ----
however my screen saver is idle and the power configurations are handled . 

My screensaver configurations 
-- active screen screensaver when computer is Idle:  (disabled) 
-- lock screen when screensaver is active:   (disabled) 
My power management 
-- put computer to sleep when inactive for: (never) 
-- spin down hard disks when possible: (disabled) 
-- put display to sleep when inactive for: (never) 

i observed that problem happened with all Linux previews versions. 
even i thought it could be resolved from Bois page, put i failed. 

really this problem makes me feel like a loser. i hope that i can get  help from you.. 

p.s. my VGA card is inboard Asus M-Board P4S800-MX  64M 

thank you everybody.

---

### Post by Giblet5 on 2009-11-30
```
xset s off
```

or

```
xset s noblank
```

---

### Post by Alromaiky on 2009-11-30
[COLOR=Red]Oh Yeahhhhh
that's it 
Problem Resolved 
thanx My dear
You are the Best....[/COLOR]

---

### Post by Alromaiky on 2009-12-01
OoopS..!

the resolve above is temporary, it is gone after Restarting, but i searched for aother resolving, i found it , and test it , it's working good,
here it is
> sudo gedit /etc/X11/xorg.conf
the file 'll open, just copy the next words and past it then save & close.
> Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

that's all 
thanx every body

---

