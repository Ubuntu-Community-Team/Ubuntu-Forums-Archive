---
title: "Ubuntu 10.10 Startup Application Preferences behavior seems erratic"
date: 2011-05-07
forum: General Help
---

### Post by MorganRogers on 2011-05-07
I have been experimenting with Startup Application Preferences, and I am seeing some odd behavior.  I first tried setting "Automatically remember running applications when logging out".  The first time I set this and shut down, I had these running:

* Terminal session
* Evolution
* Firefox
* VMware Workstation

I expected all of these to reload the next time I booted.  I was wrong.  It only started the terminal session and Firefox (see my previous thread - Firefox is restoring tabs, not home page, I don't know if this is related).  Why would this be ?   

Related note - I tried to define Evolution in the Startup Programs tab, but I can't determine what binary I should specify.  Looking in /usr/lib/evolution/2.30, I do not see an obvious executable for the main evolution app.

Appreciate any feedback, I am sure someone here has been through this.

---

