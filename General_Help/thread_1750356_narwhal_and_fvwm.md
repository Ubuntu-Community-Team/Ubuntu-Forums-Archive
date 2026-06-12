---
title: "narwhal and fvwm"
date: 2011-05-05
forum: General Help
---

### Post by brilyant on 2011-05-05
I realise this will be considered blasphemous in certain quarters but...

I would like to use FVWM in place of Compiz in Narwhal.  The usual "fvwm --replace&" works within a session, but after logging out and back in again Compiz is in charge.

I gather the "save session" stuff isn't available in Narwhal, so I'm going to have to learn what's really going on under the bonnet this time.

Could anyone offer me a clue where to start?

Thanks,

Andrew.

---

### Post by msrinath80 on 2011-05-05
Try fooling around with gconf-editor. Check this key:

/desktop/gnome/session/required_components/windowmanager

OR

/desktop/gnome/applications/windowmanager

And NO, it isn't anywhere near blasphemous. You're possibly one of the very few sane folks :-)

---

### Post by brilyant on 2011-05-06
Thanks for your kind words.

I tried everything I could see in gconf-editor, but it still won't go to fvwm at login.  I have even uninstalled compiz, in the hopes of firing up fvwm by default, but it just gives me an un-managed root window.

Never mind, as long as a right-click reveals "0pen in terminal" I can cope.  Some day I'll find out what's going on.

Andrew.

---

