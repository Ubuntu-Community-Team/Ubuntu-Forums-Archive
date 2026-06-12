---
title: "Newbie with crashed user file"
date: 2010-12-07
forum: General Help
---

### Post by jinanamurti on 2010-12-07
Hey all-

I woke this morning to these delightful messages;

'could not update ICEauthority file/home/jinanamurti/.ICEauthority'

'problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256'

'Nautilus could not create the following required folders: /home/jinanamurti/Desktop, /home/jinanamurti/.nautilus'

Although I could navigate Ubuntu's desktop, it couldn't find a home folder, could recognize but not connect to the wireless network I normally use, telling me over and again 'Disconnected--you are now offline."

The browser would not open, though both the terminal and a small application like character map did open. When I tried Evolution, it said that there was no database to store my configuration, and seemed to center around a /gconf/ problem.

I installed Ubuntu last Saturday, so I am very new to this, and have no programming experience. My only guess, and it seems likely considering this seems to be a user file problem, is that I took off the setting to ask for passwords at login last night--this is the first time I have turned it on after shutting off last night. 

Any help is greatly appreciated.

jinana

---

### Post by surfer on 2010-12-07
did you login as root lately? this messes up file ownership in your home.

try:
```
$ sudo chown -R  jinanamurti:jinanamurti /home/jinanamurti/
```
(assuming jinanamurti is your username and group).

---

