---
title: "Email questions (ubuntu 12.04)"
date: 2012-09-16
forum: General Help
---

### Post by Wim Sturkenboom on 2012-09-16
Sorry, I don't know a better title.

System with 2 users; I use evolution (I had to install it as well as evolution-indicator to get evolution to show in the notification area (or whatever it is called; right top) and my wife uses thunderbird.

1)
When we click the email icon in the right top, we both now have options for both email clients. I want to get rid of the thunderbird reference in there and she wants to get rid of the evolution one. How?

2)
The notification area does not notify the evolution user when new mails arrive. How do I set that up?

Thanks for reading and possible advice.

---

### Post by grahammechanical on 2012-09-16
I do not know if this will work. It is based upon my experience with 12.10 development branch. When I installed 12.10 it did not have Thunderbird in the Mail icon menu. Which was not much of an issue as I was using webmail instead. Once I ran Thunderbird from the Dash for the first time a link to it was put in the Mail icon menu.

So, I suggest that you un-install both Evolution and Thunderbird and then Re-install them. If you do not run Thunderbird, it may not appear in your Mail icon menu. If your wife does not run Evolution, then, it may not appear in your wife's Main icon menu.

It is just a crazy idea.

Un-installing these programs will not remove the configuration folders in the Home folder that you each have. So, when you re-install the settings and the stored emails should appear in each program as they should.

Regards.

---

### Post by SeijiSensei on 2012-09-16
Do you each have separate logins at the OS level?  I would have thought you could each configure your own desktops to use one or the other notification.

---

### Post by Wim Sturkenboom on 2012-09-17
At the moment that I installed the evolution-indicator, it showed in the notification area. So I don't think that it's going to work.

And yes, we have separate system accounts; that was obvious to me ;) Sorry for leaving that out.

---

### Post by dcstar on 2012-09-17
> **Wim Sturkenboom said:**
> Sorry, I don't know a better title.

System with 2 users; I use evolution (I had to install it as well as evolution-indicator to get evolution to show in the notification area (or whatever it is called; right top) and my wife uses thunderbird.

1)
When we click the email icon in the right top, we both now have options for both email clients. I want to get rid of the thunderbird reference in there and she wants to get rid of the evolution one. How?

2)
The notification area does not notify the evolution user when new mails arrive. How do I set that up?

Thanks for reading and possible advice.

[LIST=1]
[*]Can't be done easily, you would have to use the configuration editor to manually remove the unwanted gconf keys and then probably remove the . folders for the apps.
[*]See if the Evolution Plugin - Evolution Indicator is set up.
[/LIST]

---

### Post by Wim Sturkenboom on 2012-09-25
> **dcstar said:**
> [LIST=1]
[*]Can't be done easily, you would have to use the configuration editor to manually remove the unwanted gconf keys and then probably remove the . folders for the apps.
[*]See if the Evolution Plugin - Evolution Indicator is set up.
[/LIST]

Ad 1) Name of the editor application, please
Ad 2) How do I do that? It is installed.

---

