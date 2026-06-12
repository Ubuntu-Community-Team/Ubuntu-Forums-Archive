---
title: "Getting wine applications to see linux applications"
date: 2010-07-20
forum: General Help
---

### Post by fig_wright on 2010-07-20
I have a windows app installed under wine. It works fine. However, it has the ability to launch openoffice to do further functions. Obviously I have openoffice installed under linux, but the wine app cannot see it. How can I make the wine app see across the emulation layer into linux to see the app it needs? Dont tell me I need to install openoffice under wine as well to get it to work!

---

### Post by WorMzy on 2010-07-20
The app running under wine will be looking for an .exe in your wine prefix's "program files" directory, so installing OOo via wine is the only viable solution that I can see; and even then, I haven't tried it, so I can't guarantee that it will work.

---

### Post by byStanderone on 2010-07-20
...correct me if i am wrong, but i think wine is an ubuntu app for the purpose of running windows programs, (some) within a linux environment, and not running a linux app within wine itself.

---

### Post by Vaphell on 2010-07-20
[http://www.winehq.org/pipermail/wine-devel/2005-October/041052.html](http://www.winehq.org/pipermail/wine-devel/2005-October/041052.html)
[http://www.winehq.org/pipermail/wine-users/2005-June/018179.html](http://www.winehq.org/pipermail/wine-users/2005-June/018179.html)

smart people say it can be done - you need a dummy executable in wine environment seen by wine apps, which is a script in reality, used to invoke proper linux app. It looks quite hardcore though because you have to go around systempath issues :)

---

### Post by pzkfw on 2010-07-24
Could you explain some more on how this application integrates with open office?

If you just want to send the text to open office, you can save it as a text file, then open it in OO.org - your wine directory is /home/$(username)/.wine/drive_c/Program Files/etc.

---

### Post by fig_wright on 2010-08-11
The application itself opens openoffice and puts data into the document presented.

---

