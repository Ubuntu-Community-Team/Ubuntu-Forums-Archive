---
title: "Cant not boot into safe mode"
date: 2010-12-21
forum: General Help
---

### Post by bender6681 on 2010-12-21
First let me say sorry if this is in the wrong thread. I am a bit of a noob when it comes to linux. I was trying to figure out how to get an external monitor as my primary monitor on my laptop when i made a change that cause the desktop environment to keep logging me out. I got it into safe mode and resolved the issue but i have my account set to not ask for a password on login and it keeps booting to safe mode now. I have tried logging out and typing my username to get the option to select the normal desktop but as soon as i enter my username it boots bake in as safe mode. The option to require a password on login is not working in this mode. Anyone know how I can get this corrected?

---

### Post by bender6681 on 2010-12-22
I got it now. I went to terminal and did

sudo adduser to create a new account and then logged in as that to change my real account settings.

---

