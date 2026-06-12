---
title: "Epson SX515W printer"
date: 2009-11-23
forum: General Help
---

### Post by ambre on 2009-11-23
Hi,

Does anyone have the Epson SX515W printer/scanner printing with CUPS on Ubuntu 9.04 Server?

If so, I need a little help to get mine set up.  The instructions at AVASYS Corporation are a tad too 'power user' for this 'noob'.

Thanks,
Ambre

---

### Post by mjdenham on 2009-12-17
Hi,

I just got an Epson SX515W and to my delight it is automatically recognised by Ubuntu 9.10.

I initialised the printer via windows so that it was connected to the wireless lan and I could print wirelessly from windows.

Then I selected System/Administration/Printing and then from the menus Server/New/Printer and Ubuntu automatically 'Searched' for printers.  In the next dialog select 'Network printer' and you will see your SX510W displayed.  You will probably see 2 printers displayed - one accessed via an ip address and one accessed via DNS which will have a name like EPSON8A9B1CD.  I chose the 2nd and it worked fine.

Unfortunately the closest driver Ubuntu finds is for an Epson SX405 but it seems to work fine.

Kind regards
Martin

---

