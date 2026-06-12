---
title: "Software Sources - launch error after KDE removal"
date: 2010-08-23
forum: General Help
---

### Post by Ubunthree on 2010-08-23
I recently used the procedure on this page:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

...to scrub the kubuntu-desktop installation from my system. It worked fine (though I did have to reinstall a few packages), but now if I try to run System/Administration/Software Sources, I get an error box that says:

------------------------------------------------
**Could not launch 'Software Sources'**
Failed to execute child process "software-
properties-kde" (No such file or directory)
------------------------------------------------

Synaptic's Settings/Repositories menu still works, but I would like to fix whatever is wrong with this.

Thank You!

---

### Post by Ubunthree on 2010-08-27
Bumping.

Not a serious problem yet, as I can manage this through Synaptic, but I like things to work.

Synaptic offers a *software-properties-kde* package, so maybe I just need to install it. It seems to pull in a whole mess of KDE stuff with it, though, and I would rather fix the Software Sources glitch without doing this, if there is a way.

Thanks!

---

### Post by von Stalhein on 2010-10-16
I'm getting the same error after an upgrade to Maverick.

Didn't think I had any KDE.
Hmmmmm............

Did you get any further?

---

### Post by poubelle on 2010-10-31
I get it too, since upgrading to Maverick. I do have K3B installed, as it seems to be the only way I can burn DVDs, but otherwise no KDE stuff. 

Anyone?

---

### Post by von Stalhein on 2010-10-31
No luck here - Google was not my friend either in this instance.

---

### Post by kimchi on 2010-11-12
I get the same error on Maverick too. I'm not sure what I did to cause it.

For a workaround, you can still get to Software Sources through Synaptic Package Manager Settings menu > Repositories selection.

---

### Post by Rhizoid on 2011-08-31
I had this - it's not hard to sort out - solution below as this appeared high on a google search.

1. Right click the top panel above the menu items, choose Edit Menus.

2. Click the arrow to the left of the Applications menu to minimize it, then click the Administration menu item.

3. Find the Software Sources item under Items: click it once and then click the Properties button to the right.

4. Edit the Command: to read ```
gksudo software-properties-gtk
``` then click the close button twice.

5. Start the software sources app from the System/Administration menu.

Hope that helps someone,

Cheese!

---

### Post by von Stalhein on 2011-09-05
Thanks Rhizoid, nice job :biggrin:

---

