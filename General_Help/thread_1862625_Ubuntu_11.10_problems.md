---
title: "Ubuntu 11.10 problems"
date: 2011-10-16
forum: General Help
---

### Post by mahermali on 2011-10-16
Hi
After upgrading to Ubuntu 11.10 I found some problems:

1. when minimizing the the applications I can't see the icons on the task bar at the bottom
2. the messaging icon in the applet indicator is not found as the sound indicator
3. the most strange problem: after installing synaptic I can't run it
4. the top problem on the list: ubuntu software center is running, but when clicking on install ... it literally does nothing

What's happening here?

Regards
This forum doesn't send any notification message.

---

### Post by mahermali on 2011-10-16
for the synaptic problem the shortcut isn't work so I can run it using:
sudo synaptic

and the same thing for software center

sudo software-center

but other problems still not solved.

---

### Post by mahermali on 2011-10-17
I have another problem: running an application or more specifically a dialog it will appear in the top left of the screen behind the taskbar which means I can't move  it!!!

---

### Post by mahermali on 2011-10-17
Hi
After long long time trying to fix the problem.

I can say:

1. on ubuntu 11.04 I had the ubuntu desktop to be the default one not unity
2. upgraded to Ubuntu 11.10 then problems mentions above happened

what I ended up with mixed desktop with unity and gnome-panel even though I specify one of them at the login.

I realized with minimize problem: minimizing the windows then the windows are not displayed anywhere of the two bars (thumbnail to restore), it's like minimized in the Golden menu which is invisible.

also bars were non configurable: I can't remove panels, I can add launcher but not removing them.

the problem with launching Software center from the golden menu or the standard gnome-panel Application menu is not solved, I can't install anything and it doesn't ask for privileged access, so  I have to launch it with: sudo software-center

What I did was:
1. Enable unity during login
2. Disable gnome-panel (because I had it as a launcher in the startup applications related to previous problem)
3. Installed the applets I found in synaptic and Gwibber for twitter
4. Restart

Everything is now good but it's just Unity interface which I found it cool :cool:

Laptop used: Serval 6


I hope this will help someone someday.

by the way I have to subscribe to the thread to get the email notification. :lolflag:
Regards

---

### Post by cneil on 2011-10-17
Okay,
Here'e the solution to your audio problem.

Go to the alsamixer

Highlight the area titled <External> and push "m" on your keyboard to untoggle the must.

It worked for me. I hope that it worked for you!

[IMG]https://picasaweb.google.com/lh/photo/FmuaO_YDN63-tyQ17WewxUdq2yJLerD97GRE8DFswgE?feat=directlink[/IMG]

---

### Post by mahermali on 2011-10-18
hello cneil
thanks for your reply
The sound problem and notification area solved when I used the Unity interface but there are few more problems related to wireless and network-manager I'll put it in another thread.

thanks

---

