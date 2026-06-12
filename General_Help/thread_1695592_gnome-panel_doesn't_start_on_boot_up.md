---
title: "gnome-panel doesn't start on boot up"
date: 2011-02-26
forum: General Help
---

### Post by jondecker76 on 2011-02-26
On a fresh install of Ubuntu 10.04, there are no panels on startup.  I had to manually install gnome-panel before I could even start it from the command line.

I can get the panels restored to default pretty easy once I'm booted with ```
gconftool --recursive-unset /apps/panel && rm -rm ~/.gnome-panel && pkill gnome-panel
```. This works fine, however, the next time I reboot, the panels are missing again and I have to fix it through the terminal again.

Surely there has to be a way to get them to load automatically like they should? (I have seen a ton of posts on here about the gnome-panel problems under 10.04)

---

### Post by StephGbzh on 2011-02-26
I don't know why the gnome panels do not work in the first place but you could make your workaround run each time you boot by putting it in System > Preferences > Startup Applications.

---

### Post by coabiguy on 2011-02-26
I've run into this problem also on Ubunto 10.10.
I did a find, looking for gnome-panel
There is no gnome-panel in my search path
There is also no ~/.gnome-panel directory, no /apps/gnome directory
whence gnome-panel generates nothing
A ps -ef | grep gnome does not show anything like gnome-panel

How to I start gnome-panel?

I also don't understand your gconftool command line. I can see what it is invoking but it looks totally inappropriate for my situation.

pkill gnome-panel returns 1 because it is not running!
There is no ~/.gnome-panel directory

---

### Post by JohnnyC35 on 2011-02-28
I was having issues getting gnome-panel to start also. I wound up making a cron job to start it.

>crontab -e

   # m h  dom mon dow   command 
   @reboot env DISPLAY=:0 gnome-panel

---

### Post by Toshick on 2011-03-05
I had this panels after install, but it starts to dissapears after some system update. Now, after boot, i do "killall gnome-panel" after that it starts o.k. I think something prevents it to start at boottime. Also all icons dissapeared from my desktop. Is there are way to debug this pboblem?

---

### Post by Habitual on 2011-03-05
Once the panels are where they're supposed to be, Close all running apps, then run this from Alt+F2:
```
gnome-session-save --logout
```

That should fix it.

---

### Post by mhouck on 2011-05-20
Not working for me.  My panels disappeared after I upgraded to Natty.  I tried using PanelRestore and purging/reinstalling gnome-panel and ubuntu-desktop.  The only way I can get them to appear is if I create a shortcut to "gnome-panel" on the desktop.  Once they're there, even with the gnome-session-save, next time I logon they're gone.

---

### Post by Biokiller2510 on 2011-05-30
Hello folks, i hope I'm not to late on this matter.

I had the same problem after i upgraded to Ubuntu 10.10 and i managed to  figure a work-around for this problem, it worked for me and it has to  work for you guys:

1- Open System -> Preferences -> Startup Applications
2- Click Add
3- Write Panel in the name
4- In the Command write: bash -c "gnome-panel"
5- Add a Comment if you want to (e.g: WIN!)
6- Click Add and Restart

Regards,
Pedro.

---

