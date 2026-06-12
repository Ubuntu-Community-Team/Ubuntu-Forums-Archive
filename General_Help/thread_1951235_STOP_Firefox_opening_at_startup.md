---
title: "STOP Firefox opening at startup"
date: 2012-04-02
forum: General Help
---

### Post by Domitella on 2012-04-02
Hi there,

I'm running Ubuntu 10.4 and have for years had Firefox open on startup.  I'd like that to stop as it now takes longer to connect to the internet than it does for ff to open, so I get a load of tabs I have to refresh.

I've checked in **system > preferences > startup applications**, as suggested on other threads and firefox is not there to be deselected.  I've also looked through all the ff settings and can't find a solution.

Is there another setting which could be controlling this?

---

### Post by lovinglinux on 2012-04-02
> **Domitella said:**
> Hi there,

I'm running Ubuntu 10.4 and have for years had Firefox open on startup.  I'd like that to stop as it now takes longer to connect to the internet than it does for ff to open, so I get a load of tabs I have to refresh.?

Assuming you have the latest Firefox 11.0, open Firefox preferences, click the General tab, tick the option "*Don't load tabs until selected*" under the *Startup* section. This ill prevent the tabs from loading on startup. After you connect, just select the tab you want to open and it will magically load.


> **Domitella said:**
> I've checked in **system > preferences > startup applications**, as suggested on other threads and firefox is not there to be deselected.  I've also looked through all the ff settings and can't find a solution.

Is there another setting which could be controlling this?


That is probably because you system is using a saved session with Firefox open. To fix this you need to close Firefox and save the session with Firefox closed.

See [https://help.ubuntu.com/community/AddingProgramToSessionStartup#Session_Options](https://help.ubuntu.com/community/AddingProgramToSessionStartup#Session_Options)

---

