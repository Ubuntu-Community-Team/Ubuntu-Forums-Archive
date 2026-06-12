---
title: "The panel encountered a problem while loading &quot;OAFIID:GNOME_Panel_TrashApplet&quot;."
date: 2011-10-26
forum: General Help
---

### Post by derrickr on 2011-10-26
I quite often get the error message:

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

and am wondering if there's a long term solution to this issue?

It occurs on two of my desktops and three laptops (all running Ubuntu 10.10, in both 32 and 64 bit versions).

I must admit I haven't encountered the problem on one of other laptops running 11.10, upgraded from 11.04. However I've encountered too many other problems with those versions to 'upgrade' my main machines.

Over the years I've simply ignored this problem (or frustratingly spent hours trying to fix it), but it just keeps cropping up every now and then, with no specific pattern in terms of frequency.

It not a major headache, more of an annoyance. So, I'm wondering if there's a guru that might know of a long term fix.

---

### Post by raja.genupula on 2011-10-26
have you tried reinstalling the trash and its libraries from the synaptic ?

---

### Post by derrickr on 2011-10-26
Thanks for the reply. Yes I've done that and it seems to work - for a time. But then comes back again at some intermittent time later.

I think I can see where you're heading in terms of thinking though, in that the gnome-applets package may be becoming corrupt?

Re-installing gnome-applets and logging out then in, normally does the trick, but some time later the error message comes back again.

Unfortunately, I have no way of predicting when.

Any ideas of any relevant logs to review, when it occurs?

---

### Post by dcstar on 2011-10-26
> **derrickr said:**
> I quite often get the error message:

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

and am wondering if there's a long term solution to this issue?
........
It not a major headache, more of an annoyance. So, I'm wondering if there's a guru that might know of a long term fix.

Generally that indicates a corrupted user profile.

As another user with admin rights, you can delete the .gnome (and other relevant) folders if you don't care about your desktop configuration and let them be recreated at next login.

---

