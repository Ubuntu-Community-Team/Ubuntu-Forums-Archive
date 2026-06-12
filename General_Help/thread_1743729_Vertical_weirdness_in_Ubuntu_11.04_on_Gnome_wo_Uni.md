---
title: "Vertical weirdness in Ubuntu 11.04 on Gnome w/o Unity"
date: 2011-04-29
forum: General Help
---

### Post by Udi on 2011-04-29
**Before diving into the problem, this is my current setup:**
- Upgraded to 11.04 from 10.10
- had old installation of xubuntu-desktop (installed just this package on Ubuntu)
- Removed xubuntu-desktop before dist-upgrade. Now when turning on - I still see xubuntu 11.04.
- Disabled Unity.
- Installed and then removed Gnome3.

So now I'm with 11.04, gnome2 on Dell Vostro 3700 connected to external monitor.

**This is the problem:**
There is a vertical line, not something visible, that:
- If there's any buttons there, I can click them.
- In FileZilla for example, the cursor changes entirely, like I'm in a different window or something.
- in the limits on that "line", I cannot scroll.
- In this window for example, parts of this textarea are in that line, and when going over that line the cursor changes, nothing is clickable.

I restarted, updated and upgraded.
When Activated my laptop's monitor (Chose Separate X) everything went crazy..
So I'm still with 1 active monitor, and still have that problem.

Any thoughts? 
Any ideas what might cause this?

Thank you.

**_[COLOR="Red"]EDIT[/COLOR]_**
Solved.
I reset the xorg.conf file, too bad I didn't tried it before :)

---

### Post by Udi on 2011-04-30
Sorry for the bump,
apparently its not solved. This problem keeps coming back...

any ideas how can I solve it?

---

### Post by DevJan on 2011-05-01
Having the same problem.. Hope will be solved soon.. It's really annoying...

---

### Post by Udi on 2011-05-01
> **DevJan said:**
> Having the same problem.. Hope will be solved soon.. It's really annoying...


Hi,

What setup you have?
Did you change something (like I did)?
any special settings in xorg.conf?

---

