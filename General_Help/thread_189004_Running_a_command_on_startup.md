---
title: "Running a command on startup"
date: 2006-06-04
forum: General Help
---

### Post by nami on 2006-06-04
Hi

I need to run the following command each time ubuntu starts up

> xmodmap /usr/share/xmodmap/xmodmap.uk

Anyone know how I can do this?

nami

---

### Post by taurus on 2006-06-04
Put that line at the end of /etc/init.d/rc.local.

---

### Post by testube_babies on 2006-06-04
Are you doing this because of XGL/Compiz?  Then I would recommend System -> Preferences -> Sessions.  Go to "Startup Programs" and add it there.

---

### Post by nami on 2006-06-05
testube_babies - Yes and No

I need to do this with and without compiz!  For some reason if I don't do this, random key pressed log me out e.g. shift+a, shift + c, shift + backshape and many many more.

I know how to add a startup program but I dont know how to add this command to startup no matter what, e.g. always run this command when i login, or infact whenever ANYONE logs in.

> xmodmap /usr/share/xmodmap/xmodmap.uk

taurus - I tried that and it didnt make a difference?

nami

---

### Post by cyracks on 2006-06-05
Create a file like:
```

#!/bin/bash

 xmodmap /usr/share/xmodmap/xmodmap.uk

``` and put in */home/your-user-name/.kde/Autostart*/

---

### Post by blackjack6.21.91 on 2006-06-05
Hey just out of curiosity do any of y'all know the terminal command to run something on startup? (I'm making a shell script)

---

### Post by pommattski on 2006-06-05
So... Is there a Best Way / Best Practice for running something on startup... ??
Having searched around a little there seem to be so many ways to do it - 3 just in this thread!

In my case I need to run "xmodmap ~/.xmodmaprc" at startup and I'm using Kubuntu.

---

