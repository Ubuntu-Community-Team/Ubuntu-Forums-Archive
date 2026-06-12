---
title: "Trouble printing wireless from Ubuntu"
date: 2011-03-05
forum: General Help
---

### Post by Wuxin on 2011-03-05
I've had difficulty getting my Ubuntu laptop to print from my Brother HL 2170w printer.  When I initially set it up I was able to print the test page successfully, but beyond that nothing.  I've tried several times but I can't get the printer to respond.  What has happened, however, is that my desktop computer (a Mac-mini) has in its finder several of the attempted print jobs I made from the Ubuntu laptop!  (The format in the finder looks exactly like the Ubuntu front-end graphics.)  So all I can figure is that my router (a 2Wire) must be confused about which computer is sending the printing information.  What can I do to make the printer  understand that the command to print is coming from the laptop and not from the desktop?  Or is something else going on here that's totally beyond me?  Can anyone help out with this?

---

### Post by marshag63 on 2011-03-05
I'm assuming you are printing wirelessly.  In print server setup on ubuntu computer have you enabled, under server settings, "Show Printers Shared by Other systems"?  Then Refresh that dialog (blue circular arrow).

Now try adding a new printer, choosing network printer.  Use the printer's IP address.

Hope this helps :)


MDG

---

