---
title: "Evolution Default Browser?"
date: 2010-12-05
forum: General Help
---

### Post by jim78 on 2010-12-05
I recently installed google chrome and subsequently removed it again, and i can't find an option in evolution to change the default browser back to firefox. Am i missing something? Surely there must be one in preferences?

---

### Post by gandaran on 2010-12-05
> **jim78 said:**
> I recently installed google chrome and subsequently removed it again, and i can't find an option in evolution to change the default browser back to firefox. Am i missing something? Surely there must be onthee in preferences?
go to firefox preferences and set firefox as the default browser again, that should fix the evolution issue

---

### Post by jim78 on 2010-12-05
> **gandaran said:**
> go to firefox preferences and set firefox as the default browser again, that should fix the evolution issue

Sorry should have been more specific - It's not opening evolution from a link on the web that's the problem, it's opening a weblink in an email in evolution.

---

### Post by areteichi on 2011-01-04
I also have this problem. I have Firefox 3.6.13 set as my default browser but Evolution for some odd reason opens links with Firefox 4.0 beta. Does anyone know how to fix this?

---

### Post by dcstar on 2011-01-04
> **jim78 said:**
> I recently installed google chrome and subsequently removed it again, and i can't find an option in evolution to change the default browser back to firefox. Am i missing something? Surely there must be one in preferences?

System-Preferences-Preferred Applications-Internet

If you install the **galternatives** package:

Applications-System Tools-Alternatives Configurator-gnome-www-browser & x-www-browser

---

### Post by areteichi on 2011-01-04
I think the OP was having the same problem as I. Even if one sets the default browser in Preferred Applications menu, Evolution still opens the links with a different browser.

Besides the Preferred Applications menu, I've tried using gconf-editor and assigned /desktop/gnome/url-handlers/http to firefox but it didn't help either.

Does galternatives do something different?

---

### Post by areteichi on 2011-01-04
Ok, just gave galternatives a try and still without luck. This is a shame. Evolution is the default email client for Gnome and it can't even figure out the default/preferred browser???

---

### Post by nomko on 2011-01-04
For this kind of weird issue's with Evolution and other weird issue's i'm not a hugh fan of Evolution. First thing i always do after a new/fresh installation of Ubuntu is removing Evolution =>> System > Administration > Synaptic, search for evolution and mark evolution-common for complete remove.  Do not remove the common-server files (2x) since they are needed for the calender and more.
 
I know that Evolution is a sort of "stubborn" application which, it seems, lives by its own rules. Even though it's a good replacement for Microsoft Outlook, it still has its shortcomings.

---

### Post by DangerX on 2011-07-19
Launch gnome-control-center->Prefferred Applications then choose your web browser

---

