---
title: "I can't change read-only value in gconf-editor, howd it get read-only? How to change?"
date: 2009-11-03
forum: General Help
---

### Post by khamil8686 on 2009-11-03
Ok, so im picky and dont want to be prompted every time i click the menu with my username on it (dont know name) and a drop down menu appears and i click log out or shut down and i dont want to be prompted after that, i just want it to shut down or log out or whatever :) Before i was able to use gconf-editor and change /apps/gnome-session/options/logout_dialog to false so that it wouldnt prompt me that i will shut down or log out in 60 seconds, id rather it just log me out or shut down, but now after installing karmic a 2nd time (first time i was messing around with kde and trying to set up the suspend key on my keyboard but ended up messing up xmodmap somehow, so i went back to gnome, which im more comfortable with and kde i always seem to run into bugs) so i installed karmic a 2nd time, this time i cant change that gconf value for some reason because it became read only?
gconf editor tells me
> Could not change key value. Error message:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/gnome-session/options/logout_prompt' set in a read-only source at the front of your configuration path
when i double click the value and try to change the value. Ive tried to change the value using sudo gconf-editor to see if that had any effect, it didnt. also tried to change the value via the command line with normal permissions and using sudo. how do i change this value so it isnt read-only anymore? i havent been able to pour over the man pages about gconf-editor quite yet, just a small amount since its late and im getting tired. just hoping someone knows :) anyways, thank you for your help/attention!
btw: karmic is awesome. smoothest install ive ever had, everything worked out of the box!

---

