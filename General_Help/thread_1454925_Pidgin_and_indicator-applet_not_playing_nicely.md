---
title: "Pidgin and indicator-applet not playing nicely"
date: 2010-04-15
forum: General Help
---

### Post by xtremesupremacy3 on 2010-04-15
Hey,

So here is my problem:
In the indicator-applet next to the clock, I have a list of programs which includes Pidgin. Now it used to be a case where if I opened Pidgin logged onto the services and closed the window, it would run in the background and i could re-open the window from the indicator-applet and get notifications of people logging on etc etc.

Now for one reason or another that doesnt happen no more. I can open it through the applet, but if i close the window, it shuts the program down...also if Pidgin is running, i get NO notifications of people logging on, new messages etc.

Anyone able to help?

---

### Post by mh.hojjati on 2010-04-22
I Have the same problem , please help

---

### Post by GeorgeMurango on 2010-05-21
I'm in the same boat. I think this bug was introduced in the new pidgin update a few days ago. Before that, everything worked fine. Now Pidgin quits instead of hiding in the background when I close it.

---

### Post by Dorian17xD on 2010-05-27
For me it's worse, Gwibber stopped working with the indicator applet as well as Pidgin, if I close the window, it will close and quit instead of minimizing to the indicator applet.

The same, again, happens with Pidgin, my issue started yesterday but today it's worse :(

I think we should public this as a bug on Launchpad for the indicator-applet, I will see if there's already an open bug for this situation.

BTW, all of you are using 64 bit Ubuntu??

---

### Post by ferolvera on 2010-05-27
I had the same problem with Pidgin closing instead of minimizing to the messagin menu in the indicator applet.

I discovered a solution accidentaly while looking for Pidgin plugins in the Ubuntu Software Center: if you install the package pidgin-libnotify you will see the notification "bubbles" when contacts log in or out and the new messages too. It also seems to tell Pidgin not to close but hide when you click the close button.

Hope it heelps. Greetings.

---

