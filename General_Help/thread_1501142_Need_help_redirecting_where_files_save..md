---
title: "Need help redirecting where files save."
date: 2010-06-03
forum: General Help
---

### Post by baillou2 on 2010-06-03
Disclaimer: NOOB

I just noticed today that for some reason, a lot of stuff that is supposed to be saved under /home/ is instead being saved under my username folder. From what I can see most other users have it set up where their username folder only has the usual stuff like "videos, documents, music" etc. 
My username folder has stuff like .esd_auth (which should also be under /home from what I understand.

Please help. I'd prefer things to be saved in the right place.

---

### Post by kaibob on 2010-06-04
> **baillou2 said:**
> Disclaimer: NOOB

I just noticed today that for some reason, a lot of stuff that is supposed to be saved under /home/ is instead being saved under my username folder. From what I can see most other users have it set up where their username folder only has the usual stuff like "videos, documents, music" etc. 
My username folder has stuff like .esd_auth (which should also be under /home from what I understand.

Please help. I'd prefer things to be saved in the right place.
All those files should be under /home/username because they apply to a particular user. I just checked my /home directory, and it contained a kaibob directory and nothing else--no other directories or files. You're in good shape; don't change anything.

---

### Post by xolot1 on 2010-06-04
Yes, files relevant to individual users should be found within /home/<user> rather than /home directly.  Many programs, such as the display managers, store separate settings for different users. These configurations are stored separately, so they can easily be modified. By convention these user-specific files are found within /home/<user>. It would make sense to documents specific to yourself (such as work papers/financial documents/notes) in the user folder as well. 

When you here about someone's 'home' directory, often this is in fact /home/<user> rather than /home. Its a bit of a misnomer.

---

### Post by BoneKracker on 2010-06-04
> **baillou2 said:**
> Disclaimer: NOOB

I just noticed today that for some reason, a lot of stuff that is supposed to be saved under /home/ is instead being saved under my username folder. From what I can see most other users have it set up where their username folder only has the usual stuff like "videos, documents, music" etc. 
My username folder has stuff like .esd_auth (which should also be under /home from what I understand.

Please help. I'd prefer things to be saved in the right place.

The /home directory is not just for you; it contains the "home directories" (username directories) of each user on the system.

If you want an easy way to refer to your home directory (your username directory), you can use "~" (without quotes) anywhere you would normally have "/home/username".  Also, when you're in the terminal, and you want to go there, you can just type "cd" (instead of "cd /home/username").

---

