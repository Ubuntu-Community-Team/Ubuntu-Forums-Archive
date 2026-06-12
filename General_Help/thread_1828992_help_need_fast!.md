---
title: "help need fast!"
date: 2011-08-20
forum: General Help
---

### Post by imarubixcube on 2011-08-20
ima newbie to ubuntu, this is my second day using it. i wanted to change the ui so that my netbook would run faster, i was using compiz and when i clicked out of the app to switch to firefox my screen flashed and now i have nothing but the desktop wallpaper no toolbar, no luanch menu the super dosent even work now. how can i fix this?

---

### Post by HereInOz on 2011-08-20
Given that the machine seems to be unresponsive, I am assuming that you have done a cold reboot by cutting power to the machine then turning it all back on again?

If you haven't, please do that.  If it doesn't / hasn't fixed it, I think you are going to have to give us more information about the hardware and a fuller description of what you have done.

---

### Post by garvinrick4 on 2011-08-20
You were playing with compiz settings and got them kind of screwed up? First one resets compiz, second on unity. Try below:
ctrl/alt/F1
login
Password
```
gconftool-2 --recursive-unset /apps/compiz
```
```
unity --reset
```
ctrl/alt/F7

---

### Post by garvinrick4 on 2011-08-20
Do not just push off button when you get into a situation.
Try ctr/alt/t for a terminal to shutdown:
or ctrl/alt/F1 to get to a into a terminal.(tty)
Then you can:
sudo reboot
or
sudo halt
so as not to damage anymore:

---

