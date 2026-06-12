---
title: "gutenprint printers missing in karmic"
date: 2009-11-22
forum: General Help
---

### Post by djcarrad on 2009-11-22
hello all,

under jaunty i was running my canon ip4600 with the gutenprint 5.2.3 drivers and PPD, but after upgrading to karmic and gutenprint 5.2.4 it doesn't seem to support this printer and infact many other printers seem unsupported. that is, when i go System->Admin->Printing and try to locate PPD files, the gutenprint options aren't there. (for this printer canon has a driver that is garbage because it uses a whole heap of ink and turboprint costs, so i want gutenprint bad)
given that gutenprint claims to support this printer and other ones that don't appear to be to me and that i can't find anyone else complaining about this, it's probably some problem specific to my set up.
i've installed 5.2.4 from the source and also installed 5.2.3 from the source, but neither made a difference.

has anyone had the same problem or have any suggestions?

cheers
DC

---

### Post by XubuRoxMySox on 2009-11-23
Open a browser to [http://localhost:631/](http://localhost:631/)

Click on **Administration** (your username and password is the *computer's* username and password) and then **Add Printer** if yours is not already recognized. You can find all the PPAs there and choose the one for your printer. That oughtta do it.

-Robin

---

### Post by djcarrad on 2009-11-23
thanks for the suggestion, but it just has the same list as in the system/administration menu interface.
i do have a big list of printers, all starting with 'Foomatic'. some have 'gutenprint' in them, but the list is not how i remember it from jaunty, and it definately does not feature the one i want.
perhaps gutenprint is not installed properly, or not interacting with CUPS properly...? is there anything i can do to work that out?

cheers
DC

---

