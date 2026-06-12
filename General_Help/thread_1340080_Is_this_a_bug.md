---
title: "Is this a bug?"
date: 2009-11-28
forum: General Help
---

### Post by Umang on 2009-11-28
I just wanted to know whether I should report this (yes/no should be enough).

Sometime back, I had tried to cancel a print when the printer was out of paper. The print got canceled on the queue, but not on the printer. So I put in a sheet, which printed half a sheet and got stuck ([this happened earlier also]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/272136")). I then printed another sheet (with only a full stop, to get the stuck sheet out of the printer).

When this happened in Hardy, it was fine. But when it happened in Karmic, my printer never got off the "Out of paper" status. Even after switching off printer/rebooting, etc the print queue would always notify me that the printer was "out of paper", before printing (although it would always print, after a delay of a few seconds that is).

After getting extremely irritated, I deleted that printer from the Printing dialog and installed another. It now works fine (printer prints almost as soon as I click print).

But until I deleted that printer, I faced this problem. Should I report it, because it will affect other users also.

(Off-topic) Finally, could someone explain to me why [this bug]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/272136") cannot be fixed. I've actually reopened it, because (as I wrote on the bug), I noticed on a certain other OS I was offered to cancel a print when the printer ran out of paper. This would be a very useful feature. Why can't cups handle this?

---

