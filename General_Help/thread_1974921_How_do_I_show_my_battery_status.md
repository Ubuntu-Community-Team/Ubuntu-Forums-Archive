---
title: "How do I show my battery status?"
date: 2012-05-06
forum: General Help
---

### Post by Hwensta on 2012-05-06
OK so Im testing out Linux. I got that wubi thing. I think thats what its called. And I basically downloaded all the defaults. Im running Lunix on a laptop and for the most part I seem to be enjoying it but theres one thing thats bugging me. I cant see my battery life. Is there anyway I can see it or add an icon somewhere that will show it?

---

### Post by StApnea on 2012-05-06
Under System Settings > Power ( or just type in power in the dash) is the control for when to show the battery.

---

### Post by jadtech on 2012-05-06
the battery indicator is usually on topon the menubar next to the network menu and wireless indicator ..

when the the lap top is plugged in  and  battery is 100% full it shows up white with a plus and  when it under 100% or charging it shows dark with a white plus ..

---

### Post by Hwensta on 2012-05-06
> **StApnea said:**
> Under System Settings > Power ( or just type in power in the dash) is the control for when to show the battery.

The status bar is the bar on the top right? It's set to show up but its not showing up

---

### Post by StApnea on 2012-05-06
Does it show if you run Ubuntu from a live Cd? If you can get it to show under a live CD and not Wubi, it may be because of Wubi. If it doesn't show on either it is probably a driver issue. Those can sometimes be solved with Additional Drivers under System Settings.

---

### Post by guestolo on 2012-05-06
Found same problem
What happens if you type, or copy/paste the following into terminal

**gsettings list-recursively|grep settings-daemon**

When you get the results, either post them here
or let us know what the following is set too
[COLOR=Red]org.gnome.settings-daemon.plugins.power active[/COLOR] (true or false?)

---

### Post by llamabr on 2012-05-06
Here's the problem with starting a new thread to ask the same question again.  You cause people to duplicate their efforts.  I answered your question twice in your other thread of the same topic.

---

### Post by llamabr on 2012-05-06
It's not necessary to PM everyone to solve this problem. Just continue working through the suggestions that you get here (and confusingly, on the other thread you started with the same topic), and you'll get the best advice.

---

### Post by jadtech on 2012-05-06
i can tell you now I had 2 wubi installs I did have  the bettery indicator  though it was not always  giving the best readings  a few time it did vanish but a reboot solved the issue..

some time I would switch to window do a defrag keep inmind  wubi install is nothing but a window program more or less and you are still at the mercy of windows issues a wubi install will give you a feel for linux but is only a virtual machine though it can be mirgrated to it own parttion later on :)

---

