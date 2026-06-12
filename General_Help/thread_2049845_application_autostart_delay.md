---
title: "application autostart delay"
date: 2012-08-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-29
so i have compiz as a startup application on my xubuntu install, it appears to be delayed a few seconds is there a way to make it run sooner, the way it is now it waits for the entire desktop to load before runnning, i want it to run more seamlessly
is there some other location i can put my compiz --replace command to make it run sooner at login

---

### Post by pqwoerituytrueiwoq on 2012-10-16
I found the script i needed to edit /etc/xdg/xfce4/xinitrc
xfwm4 is started at line 144
This command will make xubuntu use compiz instead of xfwm4 (if you are not using xfce4-session)
```
sudo sed -i 's/xfwm4 --daemon/compiz \&/' /etc/xdg/xfce4/xinitrc
```if you don't per-configure compiz the gest account will be a pain to use (no window borders, movable windows, etc)
add *compiz &* on line 92 if you are using xfce4-session
this command will tell you if you are using xfce4-session
```
ps -e|grep xfce4-session
```edit:
not working as well as i hoped
i had it run a script i made instead of launching compiz 
i made it run [FONT=Courier New]Compiz &[/FONT] before [FONT=Courier New]xfce4-session[/FONT] on line 109
note the capital C in Compiz ([FONT=Courier New]/usr/local/bin/Compiz[/FONT]) that is to prevent conflict with [FONT=Courier New]/usr/bin/compiz[/FONT]
```
#!/bin/sh
echo "-------------New-Session-------------" >> /tmp/compizLog
compiz --replace >> /tmp/compizLog
STATUS="$?"
echo "Compiz exited status code: $STATUS" >> /tmp/compizLog
while [ ! $STATUS -eq 0 ];do
    sleep 2
    echo "---------Crash-Detected------------" >> /tmp/compizLog
    compiz --replace >> /tmp/compizLog
    STATUS="$?"
    echo "Compiz exited status code: $STATUS" >> /tmp/compizLog
done
echo "-------------End-Session-------------" >> /tmp/compizLog
exit
```

---

