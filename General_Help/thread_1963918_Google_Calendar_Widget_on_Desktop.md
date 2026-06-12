---
title: "Google Calendar Widget on Desktop"
date: 2012-04-23
forum: General Help
---

### Post by charlescarroll1 on 2012-04-23
I'm currently using Ubuntu 11.10 with Gnome 3. What I'd like to do is have a Google Calendar widget on my desktop so that I can visually see my calendar as well as any appointments or assignments that I have due.

I looked around a bit and found screenlets. The only widget I found was 'gcalscreenlet', which for some reason doesn't work. No widget appears after I double click on the icon from the Screenlets Manager window.

I would like to either find a comparable widget that works, or different application that would work for what I'm trying to do. I'd rather not go back to have a giant paper calendar that sits on my desk (I feel we live in a day and age where these are unnecessary, ya dig?). Does anybody have any suggestions or recommendations at all?

Thanks! :)

---

### Post by 11jmb on 2012-04-23
I know people have been able to sync sunbird with their google calendar account, but I'm not sure there is an ubuntu desktop widget available to show a Sunbird calendar

---

### Post by LewisTM on 2012-04-23
With Cairo-Dock you can create a weblet that displays a web page on your desktop without title or scroll bars.
Use this address in the config to display the mobile version of Google Calendar which has a small screen footprint.
[http://www.google.com/calendar/gp?source=mobileproducts](http://www.google.com/calendar/gp?source=mobileproducts)
It might be possible to do this with some other screenlet software but Cairo fills the task for me and is an awesome dock app.

Cheer!

---

### Post by zombifier25 on 2012-04-23
> **LewisTM said:**
> With Cairo-Dock you can create a weblet that displays a web page on your desktop without title or scroll bars.
Use this address in the config to display the mobile version of Google Calendar which has a small screen footprint.
[http://www.google.com/calendar/gp?source=mobileproducts](http://www.google.com/calendar/gp?source=mobileproducts)
It might be possible to do this with some other screenlet software but Cairo fills the task for me and is an awesome dock app.

Cheer!
I think screenlets DOES have a web frame widget to display Google Calendar like LewisTm posted above.
If you can't find it in screenlets, run this in the terminal
```
sudo apt-get install screenlets-pack-all
```

---

