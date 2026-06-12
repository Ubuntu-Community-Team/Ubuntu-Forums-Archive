---
title: "Change time from command line???"
date: 2011-05-15
forum: General Help
---

### Post by ?#Yhf%*&amp; on 2011-05-15
I decided to install Chromium OS to my dad's netbook, and it works perfectly. The only problem is that i can't change the time. Luckily, I can access a command line by pressing CTRL+ALT+T. So maybe I can change it from the command line.

Can anyone help? What command changes the time? :(

---

### Post by dino99 on 2011-05-15
usually we right click on date/time in tray to set prefs

---

### Post by Rubi1200 on 2011-05-15
Hi,
I think you can do it like this:
```
date --set="2002-6-29 11:59 AM"   
```
Obviously, this is just an example, you need to set the correct date and time on your system.

---

### Post by tredegar on 2011-05-15
The **date** command shows, or sets the time from the terminal.
You'll need to be root to set the time.
See **man date** 
eg **sudo date --utc 05141742 2011 .00**

---

### Post by ?#Yhf%*&amp; on 2011-05-15
Thanks a lot! It turns out I forgot to run it as administrator. Also, you have to log out and back in again to make the clock in the browser to show the time correctly.

I guess that's why Chrome OS isn't out yet...

For the record, I did this:
```
sudo date --set "15 MAY 2011 1:40 PM"
```

Thanks again! :)

---

### Post by Rubi1200 on 2011-05-15
Nice one! Glad you got it sorted out :-)

---

