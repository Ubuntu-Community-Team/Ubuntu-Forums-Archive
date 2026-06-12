---
title: "Startup Applications &amp; Sleep Command"
date: 2010-05-15
forum: General Help
---

### Post by rossbielski on 2010-05-15
I am trying to make chrome open up automatically after I sign in. It works but it starts too quickly. The network connection isn't established before it opens up all the startup tabs.

I tried to just add in the sleep command to the command portion of the entry but it's not working. It looks like this

sleep 5 & chromium-browser

I want chrome to wait 5 seconds after I log in to catch up the the network connection, but it never executes! What am I doing wrong? That command works fine from the command line after login, but not not from the startup applications:(

---

### Post by Vibys on 2010-05-15
Have you tried 'sleep 5 && chromium-browser' ?

edit: sorry, just looked at your screen shot, seems you have. I don't know then.

Edit: create a script to sleep and run the program and call the script from the startup applications GUI. 

Related threads: [http://ubuntuforums.org/showthread.php?t=890170](http://ubuntuforums.org/showthread.php?t=890170)
                 [http://ubuntuforums.org/showthread.php?t=396972](http://ubuntuforums.org/showthread.php?t=396972)

---

### Post by rossbielski on 2010-05-16
That did it! Thanks for the help.

---

