---
title: "Cannot logon &quot;No irq handler for vector (irq -1)&quot;"
date: 2012-04-28
forum: General Help
---

### Post by D.Dadsgé on 2012-04-28
i was just checking out the preinstalled themes for window-layout and then my account just logged out. When i try to log in again i get a quick error message "No irq handler for vector (irq -1)" and then it goes back to the login screen. i have another account on the computer which works just fine. but this last one has no rights so i need to be able to use my main account..

anyone know this problem?

i've already searched around the web an found it is a driver error but as i can log in with the other account the driver should be working fine?

---

### Post by Toz on 2012-04-28
It might be a problem with the window manager theme you selected. Try this:

1. Ctrl+Alt+F1 to go to the text login screen
2. Login using your account username/password
3. Type this in to edit the xfwm4 config file:
```
nano ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
```
4. Arrow down to the line starting:
>  <property name="theme" type="string" value=
...and change the window manager theme name after the last value to "Default" so that it reads like this:
```
<property name="theme" type="string" value="Default"/>
```
5. Ctrl+x to save the file and when prompted, press "Y" (for yes)
6. Ctrl+Alt+F7 and try logging in again.

---

### Post by D.Dadsgé on 2012-04-28
aah thank you! i was searching all over to find where i could adjust the theme in xfce :D that just did the trick!
do you also know why this happend? i dont want to get the same problem again if there is a way to fix it :)

---

### Post by Toz on 2012-04-28
What version of xubuntu are you using? Do you remember the name of the window theme? A while back there was a theme that would crash xfce - but I don't remember the name off hand. It was listed as a bug. Perhaps its the same theme or maybe you've found another one.

---

### Post by D.Dadsgé on 2012-04-28
i think it was the theme called 'Wildbush'. i guess just deleting it would do it :) and i think i installed the latest version of xubuntu :)

---

### Post by Toz on 2012-04-28
Yep. That was the one. Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/xfwm4-themes/+bug/573516]("https://bugs.launchpad.net/ubuntu/+source/xfwm4-themes/+bug/573516"). Deleting it would be best.

---

### Post by D.Dadsgé on 2012-04-28
ok thanks for the help!

greetz

---

