---
title: "Question about themes-"
date: 2009-11-09
forum: General Help
---

### Post by blur xc on 2009-11-09
How do you make them available to all users?

I've installed a bunch of themes on my user, but I don't see them on other user accounts.  I imagine they are somewhere in my home folder, but would like them available globally to all users.

Thanks,
BM

---

### Post by JugglinPhil on 2009-11-09
Your themes are in the folder /home/username/.themes. The dot makes it invisible, to view it hit ctrl+H. To make the themes accessible for other users copy the .themes folder into the home directory of the other user, choose merge folders, then choose skip the ones that are already there when it prompts you. 
You could also login as another user and install them manually, but I believe that's not what you want.

---

### Post by blur xc on 2009-11-09
That'll work.  Where are the default system themes located?  Does the OS copy the files to a ~/.themes folder for each user account that's created?

Thanks,
BM

---

### Post by JugglinPhil on 2009-11-09
Default themes are stored in /usr/share/themes.

---

### Post by blur xc on 2009-11-09
Thanks!

BM

---

### Post by JugglinPhil on 2009-11-09
You're welcome.

---

