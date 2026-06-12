---
title: "Karmic to Karmic  Samba printers not visible"
date: 2009-11-27
forum: General Help
---

### Post by PeggySue on 2009-11-27
OK I give in!  I have searched the forums but can't fix this.

I have a laptop connected wirelessly via a Dlinkrouter to a desktop which has 2 USB printers attached.
Both computers run Ubuntu 9.10.
I use the same username and password on both computers.
The computers communicate OK using SSH or with NFS.

I try to add a printer on the laptop.  Browsing the windows samba shares finds the workgroup and the host desktop machine but not the printers.

The System|Administration|Printing properties on the desktop computer shows that the printers are shared but says "Not Published.  See server settings".  However the settings menu has no option to publish.

Any ideas would but gratefully received.

P.S. I have just tried again before posting and now adding a printer can't even find the Workgroup!  This used to work fine in 8.10.

---

### Post by PeggySue on 2009-11-27
It's OK I have found the fix.

When it says "see server settings" it doesn't mean the settings tab of this window.  It means go back to the printer configuration to find server settings.

So in System|Administration|Printing under the server tab and settings set the desktop to publish.  Similarly on the laptop set "Show shared printers".

---

