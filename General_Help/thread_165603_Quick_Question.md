---
title: "Quick Question"
date: 2006-04-24
forum: General Help
---

### Post by Harold P on 2006-04-24
Okay, I'm running 5.10 Breezy Ubuntu with Gnome, and I've grown fond of KDE. So I have decided to make the switch (to Kubuntu, of course), but with the switch I have one question:

Is there a faster way to install Kubuntu rather than burning my kubuntu installation CD and write over Gnome'd Ubuntu?

Thanks,
Harold

---

### Post by gingermark on 2006-04-24
If you do a 'sudo apt-get install kubuntu-desktop" you'll install Kubuntu. Your menu might be a bit of a mess with GNOME + KDE apps though.

It'll be quicker, as you won't have to download the ubuntu base (which is common to bother versions)

---

### Post by Harold P on 2006-04-24
Is it safe enough to leave on overnight?:-k  I have to leave in a few minutes.

Thanks for replying,
Harold

---

### Post by gingermark on 2006-04-25
Oops :mrgreen:  And 8 hours later......

Yeah, it is. You'll have to choose whether you want GDM or KDM, but that's it.
GDM is the login screen you currently have for all intents and purposes. KDM is blue.

You can only shutdown from inside KDE using KDM, and you can only shutdown from inside GNOME using GDM. You can always log out, and then shutdown though.

These are the main differences as you will experience them - the decision on which to choose is hardly life or death.

---

### Post by Harold P on 2006-04-25
Okay, thanks.

I'll run it in terminal now. :)

Regards,
Harold

---

### Post by Harold P on 2006-04-25
Oh gosh!

[IMG]http://img174.imageshack.us/img174/4624/screenshot8dj.png[/IMG]

Edit--Do I restart, and will it bring me to the KDE login, and log me into the KDE? (I selected KDM)

---

### Post by gingermark on 2006-04-25
After you selected KDM the process should have completed.
And yes, the next time you start X (so when you reboot) KDM will be loaded instead of GDM.

You can then select KDE or GNOME (by clicking "Session Type")

---

