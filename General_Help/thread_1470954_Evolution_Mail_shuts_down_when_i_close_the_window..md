---
title: "Evolution Mail shuts down when i close the window."
date: 2010-05-03
forum: General Help
---

### Post by Squeazer on 2010-05-03
Here is the bug: When you close the windows of the Mail client (or go to File-->Close window) it exits the program, which is not supposed to happen. For instance, if you open up the Chat or Broadcast app, when you close the windows, they are still running (sou you still apear online and recive messages). This is not the case with Evolution Mail however. So if you want the auto mail checking to work, you have to keep the window opened. How do you get around that?

Oh and one more thing, is Push mail available? So you get notified of new messages instantly... Thanks! :KS

---

### Post by Squeazer on 2010-05-03
Bump. Any ideas guys?

---

### Post by Squeazer on 2010-05-03
Last bump. Still no body?

---

### Post by moviemaniac on 2010-05-03
> **Squeazer said:**
> How do you get around that?

You don't. It's the norm a program closes when you tell it to close. A few applications get minimized to the tray, but that's the exception from the rule. You might want to file a wishlist bug upstream.

> **Squeazer said:**
> Oh and one more thing, is Push mail available? So you get notified of new messages instantly... Thanks! :KS

Yes, with the Exchange 2007 connector. However I do NOT know if that already works with lucid's outdated version of evolution (2.28 ). You've gotta try that.

---

### Post by AcIDx0 on 2010-06-02
This happens to me too. But here's something more weird - this did not happen when I first made a clean install of lucid. Then, after several updates the bug came up. I am pretty sure it was introduced in one of the updates.

Yes, it is pretty annoying.

---

### Post by antenna on 2010-06-02
It's fairly inconsistent though if you have some apps that close when asked and some that don't... I would say it is best if they close when you tell them to.  

I just keep Evolution on my 6th workspace and it's out of the way.

---

### Post by LowSky on 2010-06-02
there is an applicatin called Alltray that can make any application minimize to tray. As far as I remember it wont work with compiz though.
and I just turn down the receive new message thing down to 1 minute. Nothing can be really that time sensitive that you cant wait 1 minute

---

### Post by cek1227 on 2010-09-06
The rub is that Evolution has both a "Close Window" and a "Quit" option. I, too, expect "Close Window" to keep the app running, especially considering a separate option for "Quit."

---

### Post by gvoima on 2010-09-11
I use this: [Evolution tray]("http://gnome.eu.org/evo/index.php/Evolution_Tray"), to minimize evolution. And I recommend upgrading to evolution 2.30.3 from the [evo230]("https://launchpad.net/~jacob/+archive/evo230") ppa, as it support imap+ (which supports imap idle that many of the email providers use, it's very similar to push for user perspective. Gmail etc.).

---

### Post by repunante on 2010-10-01
I've found a turnaround here:
[http://www.taringa.net/posts/linux/5613839/Minimizar-Evolution-a-la-barra-de-notificaciones.html](http://www.taringa.net/posts/linux/5613839/Minimizar-Evolution-a-la-barra-de-notificaciones.html)
They use Devil's Pie and it looks like it is working but I didn't use it enough to have a complete feedback.
It is in Spanish but I think it is easy to understand. If someone struggle I could translate it, let me know.

---

### Post by Andras B. on 2010-12-14
> **repunante said:**
> I've found a turnaround here:
[http://www.taringa.net/posts/linux/5613839/Minimizar-Evolution-a-la-barra-de-notificaciones.html](http://www.taringa.net/posts/linux/5613839/Minimizar-Evolution-a-la-barra-de-notificaciones.html)
They use Devil's Pie and it looks like it is working but I didn't use it enough to have a complete feedback.
It is in Spanish but I think it is easy to understand. If someone struggle I could translate it, let me know.

Excellent solution, I tried it myself. Works almost as expected, worth mentioning though that this method merely hides the Evolution window from taskbar, nothing more. You still have to start it, and if you close it with X button, it will be gone. You have to minimise, not close, to hide the window.

Would be nice if Evolution too had a "close to messaging area" option in preferences.

---

### Post by repunante on 2010-12-14
I know about that, that's why I quit Evolution time ago and now I focus completely on Thunderbird; with it I managed to synchronised address book and calendars and there are a lot of possibilities to minimize it to the tray.

---

