---
title: "Epiphany 2.28.0 and hotmail"
date: 2010-02-06
forum: General Help
---

### Post by madwoollything on 2010-02-06
I'm looking for an extension that will allow me to open my hotmail account without encountering the annoying 'Upgrade Your Web Browser' message, as hotmail only recognises firefox, safari & IE.

I've been looking through the epiphany documentation and googling for extentions that will allow epiphany to appear to be one of the standard web browsers when interrogated by the hotmail site ...... but with no success so far. Any suggestions (other than don't use hotmail)?

(I've also been trying to do the same thing with Arora web browser so again I can access hotmail without the 'upgrade your web browser' message ...... any ideas? I think I'm looking for something called 'User String Agent'????)

---

### Post by madwoollything on 2010-02-07
One solution is to upgrade to a later version of epiphany 2.29.6 from the launchpad site. [https://launchpad.net/~webkit-team/+archive/epiphany]("https://launchpad.net/%7Ewebkit-team/+archive/epiphany")

This later version allows you to set the user_agent value in gconf-editor to 'firefox' which can be found under /apps/epiphany/general. Just launch gconf-editor from the command line.

(There is probably a way to use about:config to do this but this appears to be broken in both versions of epiphany listed here)

---

### Post by coolbrook on 2010-02-08
Awesome

---

