---
title: "MeMenu broadcast functionality not active"
date: 2010-07-01
forum: General Help
---

### Post by tfotherby on 2010-07-01
Hi,

I have a question about the "*general broadcast accounts utility*" in the MeMenu which I have read about at [https://wiki.ubuntu.com/MeMenu](https://wiki.ubuntu.com/MeMenu).

Even though I have added 3 broadcast accounts the MeMenu status is disabled and there is no textbox where I can enter my status. Here is a screenshot:

[IMG]http://www.tomfotherby.com/Images/20100701_MeMenu_unactive_issue.jpg[/IMG]

Gwibber (Applications -> Internet -> Gwibber Social Client) as a stand alone application works fine but I would like the MeMenu to also work.

Anyone know what I have done wrong or how to fix it?

It has been like this ever since I upgraded to 10.04. I have checked "*gwibber-service*" is installed and running.

Cheers,
Tom

---

### Post by colorlessprism on 2010-07-01
you might try opening gwibber and seeing if the text box appears. if it does then you will need to add "gwibber-service" to your startup applications. some people report success with just checking the "start service at startup" option in the gwibber settings, while other have to manually add the service.

---

### Post by tfotherby on 2010-07-03
> **colorlessprism said:**
> you might try opening gwibber and seeing if the text box appears. if it does then you will need to add "gwibber-service" to your startup applications. some people report success with just checking the "start service at startup" option in the gwibber settings, while other have to manually add the service.

Yes you're spot on - once I open the qwibber application, the text box appears in the MeMenu. Even when I close qwibber the text box remains in the MeMenu until the next reboot.

I went to System->Preferences->'Startup Applications' and added "gwibber-service" and then rebooted but it didn't fix the issue. "ps -A | grep gwibber" shows nothing after the reboot. I wonder if this is because I have automatic login turned on and perhaps it can't run until the gnome keyring is unlocked?

Anyway, thanks for the workaround. Now I know I just have to go to the command prompt and type "gwibber-service" in order to get the text box to appear in the MeMenu. I still don't get any notifications when someone I follow posts a tweet but I think that might be a different issue.

---

### Post by colorlessprism on 2010-07-03
i have the automatic login and gwibber started for me (i no longer use it) my problems were fixed when i opened the gwibber preferences and checked "enable service at login". gwibber is very promising, but i just dont think its quite ready

---

