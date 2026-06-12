---
title: "Since upgrading to 12.04 my computer won't power down"
date: 2012-05-22
forum: General Help
---

### Post by kudzu on 2012-05-22
Hey everyone,

I upgraded from Ubuntu 9.10 to 12.04 a couple of weeks ago, and since then my computer doesn't always power down completely when I try to shut it down. Sometimes it does power down like it should, but other times the screen goes dark while the power light under the monitor stays on and the computer continues to run. I've left it like this for hours, and it still stays on. If I want to turn off my computer I have to hold the power button down.

I've seen a few posts mentioning this issue around the web, but no one seems to have come across an answer. Several of the people dealing with this problem have the same computer as me - a Dell Latitude D630 - but others have different computers.

I'm at a loss as to what could be causing this problem. I've tried shutting down from Unity, and I've tried shutting down from Gnome Classic. The problem seems to be independent of the GUI.  Does anyone have any ideas?

---

### Post by garvinrick4 on 2012-05-22
What happens when you open a terminal and:
```
sudo shutdown -h now
```

make -h  an -r and it restarts your machine.

---

### Post by Lynceus on 2012-05-22
This is a known issue, and i had the same problem

The code given above should help though

---

### Post by kudzu on 2012-05-22
I tried the restart version of code, but just as before, my monitor turned off and yet my computer continued to run. I had to hold down the power button to turn the computer off and then press the button again to turn it back on.

---

