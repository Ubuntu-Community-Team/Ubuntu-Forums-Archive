---
title: "Nautilus lag after xubuntu-desktop install/remove"
date: 2011-06-23
forum: General Help
---

### Post by r_ramjet on 2011-06-23
Hi 

I'm running Ubuntu 11.04. The other day i decided to try out Xubuntu, so installed the xubuntu-desktop package via synaptic. This automatically removed the ubuntu-desktop package. Xfce was interesting enough to try out - but when i switch back to a Ubuntu classic session, nautlius is really laggy when opening folders. The content of the folders are displayed, but the "wait cursor" persists for 5-10seconds. Quite annoying.

I have re-installed the Ubuntu-desktop package, but this did not fix the problem. 

Any suggestions?

THanks.

---

### Post by wildmanne39 on 2011-06-23
> **r_ramjet said:**
> Hi 

I'm running Ubuntu 11.04. The other day i decided to try out Xubuntu, so installed the xubuntu-desktop package via synaptic. This automatically removed the ubuntu-desktop package. Xfce was interesting enough to try out - but when i switch back to a Ubuntu classic session, nautlius is really laggy when opening folders. The content of the folders are displayed, but the "wait cursor" persists for 5-10seconds. Quite annoying.

I have re-installed the Ubuntu-desktop package, but this did not fix the problem. 

Any suggestions?

THanks.Hi, two things if you are using desktop effects through compiz, in classic it needs to be replaced with the older version and I will give you a link for that, and if you setting just got changed you can try this.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.


[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by r_ramjet on 2011-06-23
Thanks. I ended up doing this:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

which seems to have worked, although not without it's side-effects. 


The tips you posted did help me fix (at first glance) some Vsync issues i was having with XBMC -  bonus!

Cheers

---

### Post by wildmanne39 on 2011-06-24
> **r_ramjet said:**
> Thanks. I ended up doing this:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

which seems to have worked, although not without it's side-effects. 


The tips you posted did help me fix (at first glance) some Vsync issues i was having with XBMC -  bonus!

CheersHi, your welcome, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

