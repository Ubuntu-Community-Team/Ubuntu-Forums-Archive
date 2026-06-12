---
title: "Reduce the default shutdown countdown"
date: 2009-11-06
forum: General Help
---

### Post by praveenthivari on 2009-11-06
I want to reduce the default  countdown during shutting down. It is 60sec now. I want to make it zero, how do I do it???:p

---

### Post by t0p on 2009-11-06
I don't know how to do that.  But (assuming Karmic is the same as Jaunty) you don't have to wait for the countdown to reach zero before the system shuts down.  On the notification box that contains the countdown, there's a button labelled "Shutdown now" or some such thing.  Click that button.  System shuts down straight away.

---

### Post by danill2008 on 2009-11-06
> **praveenthivari said:**
> I want to reduce the default  countdown during shutting down. It is 60sec now. I want to make it zero, how do I do it???:p

You can Right-click on the Shutdown button at the Corner, then open preferences and Uncheck "Show confirm dialogs for Logout, Restart and Shutdown". It then remove the dialog for shutting down;)

---

### Post by 101011010010 on 2009-11-06
Hello there,
> You can Right-click on the Shutdown button at the Corner, then open preferences and Uncheck "Show confirm dialogs for Logout, Restart and Shutdown". It then remove the dialog for shutting downYou can't do that in Karmic.There's no Preferences option.

---

### Post by Wobblybob on 2009-11-06
Remove the 60 second to shutdown confirmation message in Karmic

Open a [Terminal] and type gconf-editor and press [Enter], now using the left-hand menu select [apps], then [indicator-sessions] and tick the box next to [ suppress_logout_restart_shutdown ]

---

### Post by praveenthivari on 2009-11-06
Thanks for the replies:p:p:p

To Wobblywob:
It worked.:p
Just out of curiosity : Can I just reduce the countdown to my needs?

---

