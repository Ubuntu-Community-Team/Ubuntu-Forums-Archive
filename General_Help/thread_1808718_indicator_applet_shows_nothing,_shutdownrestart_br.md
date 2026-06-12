---
title: "indicator applet shows nothing, shutdown/restart broken"
date: 2011-07-20
forum: General Help
---

### Post by rrwo on 2011-07-20
For reasons that I do not understand, the xfce indicator applet has stopped working. It's not visible, so I cannot see thinks like the wireless applet.

I can't find anything from searching the net.

I suspect that it has something to do with dbus.

Perhaps it's related, but whenever I choose to shutdown or restart,  it now goes back to the GDM login screen instead. I've had this problem before on earlier Ubuntu distros, but I don't remember how to fix it.

---

### Post by Toz on 2011-07-20
Is there anything of relevance in your **~/.xsession-errors** file? 

The issue about shutdown/restart going back to a login screen is a known (albeit intermittent for some) bug. It is being worked on upstream.

---

### Post by JKyleOKC on 2011-07-20
It may have somehow been removed from the panel. Try right-clicking on the panel and select "Add New items..." from the resulting context menu, then scroll down the list to the "Notification Area" listing, and drag its icon to the panel. That should install it, and if it had been removed should solve your problem. If it's visible but still doesn't work, then I have no other suggestion...

---

