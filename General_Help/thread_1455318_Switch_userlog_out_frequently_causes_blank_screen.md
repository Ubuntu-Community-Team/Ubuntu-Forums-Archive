---
title: "Switch user/log out frequently causes blank screen"
date: 2010-04-15
forum: General Help
---

### Post by JimGvo on 2010-04-15
Running Hardy on a Compaq laptop.  No Visual Effects.  
lspci:

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

xorg.conf has no special device driver, probably set by default install.


If I switch user or log out, I get a blank screen most of the time.  Rarely it works.  C-A-backspace doesn't work.  Sometimes C-A-del will restart but not always.  C-A-F1 does not bring up a console.  X is hosted.  

I've seen similar threads but only with the System76 forum, whatever that is.  Nothing in those posts made seemed to be applicable or didn't help.

One other odd problem.  Sometimes if the computer is left running, after 30 minutes or a couple of hours or 20 hours or ??? It locks up.  The clock stops incrementing the keyboard doesn't do anything, however the mouse pointer moves with the mouse.  Clicking doesn't do anything however.  C-A-del and C-A-backspace non functional.  Once it hung while I was actively using it but only once.  I don't know if these problems are related.  At one time I thought it was related to the presence of a Verizon Air card, but it's failed without that card in the slot, too.

Thanks,
Jim.

---

### Post by jazzgossen on 2010-05-15
I've got essentially the same problem at logoff and user switch. However, by uninstalling gnome-screensaver I think I have solved the user-switch issue. But I still can't reliably log out when more than one user is logged in without getting stuck at a black screen.

From what I gather, the problem is related to the Nvidia and ATI drivers (I use nvidia). Still looking for a solution.

---

