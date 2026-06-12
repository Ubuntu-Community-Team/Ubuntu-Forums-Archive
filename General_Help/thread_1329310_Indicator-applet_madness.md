---
title: "Indicator-applet madness"
date: 2009-11-17
forum: General Help
---

### Post by gasparov on 2009-11-17
Hi I have some problem with the indicator applet and I'm asking for help from other users
[LIST]
[*]removing indicator-applet from startup programs still loads indicator applet
```
gas@gas-lab:~$ ps aux|grep indicator
gas       1997  0.0  0.4 246264 14984 ?        S    15:10   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=19
gas       1999  0.0  0.4 248380 15336 ?        S    15:10   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=26
gas       2011  0.0  0.1  95372  3724 ?        S    15:10   0:00 /usr/lib/indicator-session/indicator-status-service
gas       2013  0.0  0.0  42160  2360 ?        S    15:10   0:00 /usr/lib/indicator-session/indicator-users-service
gas       2015  0.0  0.0  51080  3044 ?        S    15:10   0:00 /usr/lib/indicator-session/indicator-session-service
gas       2017  0.0  0.1  64708  3944 ?        S    15:10   0:00 /usr/lib/indicator-messages/indicator-messages-service
gas       2416  0.0  0.0   7336   876 pts/0    R+   15:20   0:00 grep --color=auto indicator

```
[*]indicator applet shows up email just while evolution is running, shouldn't it check for emails by itself like a mail checker applet? I don't need an applet to show up unread mail if I have the actual email client running
[/LIST]

Thanks for your time

---

### Post by Giblet5 on 2009-11-17
> I don't need an applet to show up unread mail if I have the actual email client running

That is because you use only one desktop.

Most people use 2-4 desktops, and the email client is not visible most of the time.

The indicator applet is not an email-checker; it's an indicator applet. If you want an email checker, there are plenty of them available in Synaptic, and they're incredibly easy to write.

The indicator applet is a tardwidget and a ridiculous waste of disk space. I won't argue that point. But not for any of the reasons you stated.

---

### Post by gasparov on 2009-11-18
Well...I'd love to do that but for some reason , as i said, i cannot get rid of it.

---

### Post by Giblet5 on 2009-11-18
Go to System -> Preferences -> Startup Applications

Scroll down to "Indicator Applet".

Remove it.

Log off. Log in.

---

### Post by gasparov on 2009-11-18
> **gasparov said:**
> Hi I have some problem with the indicator applet and I'm asking for help from other users

removing indicator-applet from startup programs still loads indicator applet


That is actually my problem

---

### Post by Giblet5 on 2009-11-18
I just right-clicked mine and I see something that was never there before: "Remove from panel". Did this happen in an update? It used to be 100% retarded about right-clicks. This change makes it about 99.44% retarded - a huge improvement.

That does remove it, too. I have no use for it either.

---

### Post by gasparov on 2009-11-18
I missed that, thanks a lot

---

### Post by Giblet5 on 2009-11-18
> **gasparov said:**
> I missed that, thanks a lot

Me too. It's new (w/in the last week...)

Mark this thread SOLVED with the Thread Tools thing above.

---

