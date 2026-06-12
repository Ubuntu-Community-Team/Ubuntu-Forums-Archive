---
title: "KDE problem with password prompt."
date: 2011-10-30
forum: General Help
---

### Post by jimbo99 on 2011-10-30
I'm having issues with KDE not prompting for passwords and as a result I can't do anything unless I force the prompt.  Any clues anyone?

---

### Post by philinux on 2011-10-30
Please don't thread hijack. Start a new thread.
No worries fixed that. :)

---

### Post by peshte on 2011-11-11
I have installed Kubuntu under Windows with wubi and I have the same problem. No installs and no updates. I even don't know how to force the password prompt.

Then, I have installed Ubuntu wich works fine, then KDE. The same problem under KDE, bu Ubuntu works fine.

---

### Post by dniMretsaM on 2011-11-11
> **jimbo99 said:**
> I'm having issues with KDE not prompting for  passwords and as a result I can't do anything unless I force the prompt.   Any clues anyone?

Need to know a few things first:
What version of Kubuntu/KDE are you running?
Have you done upgrades in the past, or just fresh installs (or is this your first install)?
What are you trying to do that should be asking for the password?

---

### Post by peshte on 2011-11-12
Now I have installed Kubuntu directly from iso in virtualbox and works, the password prompt shows.
I think the problem is at kubuntu installed with wubi.

---

### Post by peshte on 2012-03-31
I've found a possible solution.
Install pollkit-kde-1 from a non-kde session and restart. Worked for me.

---

