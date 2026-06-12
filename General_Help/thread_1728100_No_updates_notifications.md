---
title: "No updates notifications"
date: 2011-04-13
forum: General Help
---

### Post by Gaba_p on 2011-04-13
Hi,

I'm running Ubuntu 10.10 + KDE 4.6.2 and the problem is that for a while now (two months or more) I don't see the updates notification icon. If I open 'kpackagekit', the updates are there. I have the 'Notifies when updates are available' checkbox checked in 'Kpackagekit' and the same checkbox checked in the 'Updates' tab in the 'Configurations' module of 'Update Manager' (which also shows the available updates by the way)

How can I get the notifications to show?

Cheers,
Gabriel

---

### Post by Blackoulis on 2011-04-13
Well...i had a same issue in ubuntu 9.10 i think..
Go to update manager,then adjustments(on the down-left side).
Make sure you do not have the live cd checked on Ubuntu software tab.

---

### Post by Gaba_p on 2011-04-13
I'm guessing you mean in the 'Other Software' tab. There is no 'LiveCD' check in 'Ubuntu software' tab.
Anyway, no, it is not checked.

---

### Post by Blackoulis on 2011-04-13
There should be an "Ubuntu software" tab next to the "other software" tab..
Anyway,check if on notifications tab the check for notification is ticked,and above that if everything except lucid backports is enabled..

---

### Post by Gaba_p on 2011-04-13
> **Blackoulis said:**
> There should be an "Ubuntu software" tab next to the "other software" tab..

Indeed there is. There is no LiveCD check in the 'Ubuntu software' tab. The closest thing is a 'CD-ROM Ubuntu 10.04 Lucyd Lynx' check in the 'Other Software' tab. This is NOT checked.

> **Blackoulis said:**
> Anyway,check if on notifications tab the check for notification is ticked,and above that if everything except lucid backports is enabled..

I guess you mean 'Updates' tab. Everything except 'maverick-proposed' is checked (I'm running maverick, not Lucid); I checked it now. 'Only notify about available updates' is checked.

After checking 'maverick-proposed' and rebooting, the icon appeared. Maybe it was just that check not being selected.

Thanks for your help Blackoulis.

---

### Post by Gaba_p on 2011-04-14
After enabling the 'maverick-proposed' packages, 'kpackagekit' started showing the icon on the system tray when there are new updates available.
So far only 'maverick-proposed' updates have been showing, so I'll wait until I get an update from another package to mark this thread as solved.

Cheers

---

### Post by Gaba_p on 2011-04-15
Ok, all updates seem to be showing so I guess it was just that (the fact that 'maverick-proposed' was not enabled)
I'm marking this one as SOLVED then.

Thanks again Blackoulis!

---

