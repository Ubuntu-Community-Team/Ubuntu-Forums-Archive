---
title: "can't select text in forms in Firefox"
date: 2010-07-21
forum: General Help
---

### Post by boddhisatva on 2010-07-21
I think it started after the last Firefox update - I can't select text in forms on any page - not even here, while I'm writing this. When I double click, the selection appears for a fraction of a second, and vanishes instantly. Neither can I select text by dragging, the same happens. I can still select everything with ctrl+A, but I can't select single words or sentences. It's driving me nuts. I've actually switched to Chrome because of this, but I'm missing a lot of Firefox's functionality there, so I'd rather stay with Mozilla. Any ideas, good people?

---

### Post by lovinglinux on 2010-07-21
Have you tried to create a new a Firefox profile?

See [http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

---

### Post by boddhisatva on 2010-07-21
I have previously tried doing a fresh install of Firefox by uninstalling all FF-related packages and manually removing my profile folder from Home. But the newly installed FF crashed soon after launch. Now I've tried creating a new profile following your suggestion, but the new-profile Firefox crashes immediately after launch. Seems like a serious problem.
Is there perhaps a way to remove ALL stuff that's related to FF and make a complete new install? I could then get my settings back manually.

---

### Post by lovinglinux on 2010-07-21
> **boddhisatva said:**
> I have previously tried doing a fresh install of Firefox by uninstalling all FF-related packages and manually removing my profile folder from Home. But the newly installed FF crashed soon after launch. Now I've tried creating a new profile following your suggestion, but the new-profile Firefox crashes immediately after launch. Seems like a serious problem.
Is there perhaps a way to remove ALL stuff that's related to FF and make a complete new install? I could then get my settings back manually.

Go to Synaptic, look for installed firefox packages and xulrunner and mark them for re-installation and apply. If that doesn't help, start Firefox from a terminal and post the error messages.

BTW, it was you that posted a comment on my site as Pawel right?

---

### Post by boddhisatva on 2010-07-21
Yes, it was me. I didn't realize it was your blog :).
Re-installing didn't help. The error I got is:

[B]Attempting to load the system libmoon 
Segmentation fault[/B]

Looks like it was related to the Moonlight extension (which I'm not sure works anyway). I've removed it and it's working! I mean the new profile. The old one still has the form issue, but I'll just manually reinstall all the extensions and stuff. Or I'll read through your blog, perhaps there are some problematic add-ons or other stuff that might cause this form behaviour.
Thanks for the suggestions!

---

### Post by lovinglinux on 2010-07-21
> **boddhisatva said:**
> Yes, it was me. I didn't realize it was your blog :).

No problem. I have deleted the message there, since we are already discussing here.

> **boddhisatva said:**
> The error I got is:

[B]Attempting to load the system libmoon 
Segmentation fault[/B]

Looks like it was related to the Moonlight extension (which I'm not sure works anyway). I've removed it and it's working! I mean the new profile. The old one still has the form issue, but I'll just manually reinstall all the extensions and stuff. Or I'll read through your blog, perhaps there are some problematic add-ons or other stuff that might cause this form behaviour.
Thanks for the suggestions!

It was definitely libmoon. I haven't seen that problem for a while, but libmoon caused similar problems to several users a couple of months ago.

If the new profile also doesn't exhibit the form issue, then most likely to be an extension causing the second problem.

Start the old profile in safe mode to be sure. If you can confirm that, then you don't need to copy all your stuff to the new profile, just need to find out which extension is causing the problem and disable it.

---

