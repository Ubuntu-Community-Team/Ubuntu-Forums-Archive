---
title: "Revert to Firefox 3.5 from Firefox 3.6pre"
date: 2010-01-21
forum: General Help
---

### Post by Nordic on 2010-01-21
I ran updates today on my recently upgraded 9.10 install, and firefox got upped from 3.5 to 3.6. However, a critical extension (OpenOffice integration for Zotero) does not work with 3.6!

How can I get back to firefox 3.5?

Eric (Nordic)

---

### Post by nikef on 2010-01-21
Just looked in synaptic package manager and 3.5 is in mine .

---

### Post by nanotube on 2010-01-21
> **Nordic said:**
> I ran updates today on my recently upgraded 9.10 install, and firefox got upped from 3.5 to 3.6. However, a critical extension (OpenOffice integration for Zotero) does not work with 3.6!

How can I get back to firefox 3.5?

Eric (Nordic)

Hi
which repository did the 3.6 update come from? it's not in the official ubuntu repositories, so it must have come from some third-party repository that you have enabled.

---

### Post by Nordic on 2010-01-21
The lights are slowly coming on in my dim little brain - The mozilla repository that I enabled in my quest for Thunderbird 3.0 (which I like) is now coming back to bite me!

I shall remove that repository, then rm firefox and try again.

Apologies for wasting y'alls time with my bone-headedness! :rolleyes: I think there is a valuable lesson about repositories and the update manager in here.

"Life is harder when you're stupid" - Andrew Hill

Nordic

---

### Post by nanotube on 2010-01-21
> **Nordic said:**
> The lights are slowly coming on in my dim little brain - The mozilla repository that I enabled in my quest for Thunderbird 3.0 (which I like) is now coming back to bite me!

I shall remove that repository, then rm firefox and try again.

Apologies for wasting y'alls time with my bone-headedness! :rolleyes: I think there is a valuable lesson about repositories and the update manager in here.

"Life is harder when you're stupid" - Andrew Hill

Nordic

hm, you are probably talking about the ubuntu-mozilla-daily repository, which tends to clobber the official-repositories versions. 

if you want to get the latest releases but not have anything clobbered, you could use the ubuntuzilla repository. if you enable it, you can install tb3, but it won't bother you with overwriting firefox, unless you explicitly install the firefox package from that repository.

take a look if you are up for it:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by adam.smith on 2010-01-22
A working Zotero Ooo plugin for FF 3.6 is available
[http://forums.zotero.org/discussion/10439/firefox-36/#Item_16](http://forums.zotero.org/discussion/10439/firefox-36/#Item_16)

---

### Post by Nordic on 2010-01-22
After disabling the offending repository, I was able to revert everything back to the way I had wanted it.

Next time I will try the Ubuntuzilla repos - I hadn't been aware of it before. Thanks all! :D

Nordic

---

