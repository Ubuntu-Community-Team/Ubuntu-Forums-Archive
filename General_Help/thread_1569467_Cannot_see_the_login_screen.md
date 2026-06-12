---
title: "Cannot see the login screen"
date: 2010-09-06
forum: General Help
---

### Post by Adrienk on 2010-09-06
So a while ago more like an hour or so again I made a thread asking for help on emerald, compiz and bla.

Well i got it all working and had to use a theme (like an actual gnome theme, as in system preferences appearance theme) and after following those instructions I got it too look like a mac except with out the whole "file, places and other menu - that part wouldn't install properly"

So i decided I would shut down the virtual machine and then reboot.

before hand though i noticed some errors:

If i try and add the clock, notifications or any of the other default items with the exception of configured menu and desktop switcher, I get this error stating that the panel had an issue or something trying to load that selected item and that i should delete it (the item) from the configuration settings or something simmalr..

See I would post the exact message its just that the login screen is BLACK, i hear the sound the computer makes when you get to the login screen and i see the cursor but everything is black. How do I log in and get to the desktop?

---

### Post by Adrienk on 2010-09-06
So isnt there a command to let you login via the terminal and then I would go startx or something?

---

### Post by Adrienk on 2010-09-06
New developments.

I cant copy and paste everything here because I don't have a cursor in the prompt.

I was able to log in and I typed in start x

and I got the error:

xinit: Resource temporarly unavailable (errno 11): unable to connect to X sever
xinit: No such process (errno 3): server error.

Upon running it again I get:

Fata Server error:
Server is already active for display 0
if the server is no longer running, remove /tmp/.X0-lock
and start again.

invalid MIT-MAGIC-COOKIE-1 keygiving up.

and then its the xinit error again.

This has all happened because of 

I installed compiz,
I Installed emerald, and then went and did the emerald command (i totally forgot what it was just now....)
I installed a theme that didnt quiet do it for me, so I used the appearance - theme under preferences to change the look of all the windows, icons and what not.

I tried to install a global menu, when that failed I used apt-get -f that installed pakages of some sort, still failed to get me the menu.

and now i cant start the xserver to start the dekstop.

I may have to re-install.


any suggestions?

---

### Post by Adrienk on 2010-09-06
I plan to just reinstall and keep doing this till I get the theme the way i want it. 
But thanks in advance for all your guys help.

I noticed

when I was running the emerald command in the terminal, if i closed the terminal that's when things started to go south, window decorations were breaking and windows could not be moved, some windows were not even opening.

So I am going to try all this again.

---

