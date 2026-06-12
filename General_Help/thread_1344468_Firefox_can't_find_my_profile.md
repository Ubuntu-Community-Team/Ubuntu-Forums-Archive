---
title: "Firefox can't find my profile"
date: 2009-12-03
forum: General Help
---

### Post by okhowaboutthisusername on 2009-12-03
Long-time Fedora/RH user here. I've just installed Karmic (nice!). I copied my .mozilla dir from my backup drive and tried starting FF but it keeps prompting my to create a profile, as if it can't see the dir. The perms on the .mozilla dir are 0700, which seemss correct. Could that be it?

Otherwise, is this a known issue? Is the problem with a file or files in the dir that should be different for Ubuntu? Google hasn't suggested this is a common problem, so I'm figuring that''s not it.

---

### Post by lidex on 2009-12-03
Might be better to create a new profile, close firefox, then copy pertinent files from your backup to the newly created profile folder. Usually works for me - even going from xp to jaunty. Another option is to backup your profile using febe extension and import into new install.

---

### Post by wojox on 2009-12-03
The profile.ini points to the *.default directory, where all the goods are.

---

### Post by okhowaboutthisusername on 2009-12-03
Thanks for the replies. I was about to follow that advice when I realised that everything inside .mozilla was owned by root. I'm not sure what happened there but doing a chown resolved the problem.

---

### Post by lidex on 2009-12-03
> ...everything inside .mozilla was owned by root...
Yeah I think that's a default behavior when moving from another hd. However I would still advise you to begin with a new profile since this is a new install on a different platform but I may just be paranoid. 8-[

---

