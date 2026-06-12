---
title: "Can't log in to Ubuntu"
date: 2010-04-12
forum: General Help
---

### Post by E&#9837;FFA on 2010-04-12
I have Ubuntu set to log in automatically, but lately when I start up my computer it tries to log in but fails (for no apparent reason; it just quits) and goes back to the login screen. So I try to log in, and it shows the progress bar and the screen flashes black a few times then it returns to the login screen again. If I keep trying again, it'll keep doing the same thing.

Sometimes though, if I restart the computer a few times, trying again that way, it'll eventually just work. But lately it seems to take more and more restarts before it works. Like it's getting worse and worse, which is weird.

I can press Ctrl+F1 and log in through the terminal just fine. I can even select the "xterm" session of Ubuntu and log in to that. (The "GNOME failsafe" session doesn't work by the way.) In fact, if I log into the "xterm" session and run `gnome-session' from there, GNOME starts up and everything appears to be working normally, as if I'd logged into the usual "GNOME" session, except the xterm window is still open and if I close it then all of GNOME closes with it.

So that's my current workaround: log into the "xterm" session, run `gnome-session`, move xterm window to another workspace and forget about it. Of course I'd prefer to be able to log in automatically like a normal person, so if anyone has any suggestions, please post!

---

### Post by LowSky on 2010-04-12
it something to try:

log in through a terminal, and run an update.

```
sudo apt-get update && sudo apt-get upgrade
```

see if that fixes your errors, you might have something that isn't quite installed correctly too. that is giving you these problems that might ge tfixed by updating

---

### Post by E&#9837;FFA on 2010-04-12
Hey, thanks. It installed a couple updates but it doesn't look like it changed anything... I still can't log in.

But thanks. Have a duck bill.

---

