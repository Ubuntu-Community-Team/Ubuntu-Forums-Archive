---
title: "Profiles"
date: 2009-08-20
forum: General Help
---

### Post by mercules2178 on 2009-08-20
I have several firefox profiles that I imported from windows. I can access them from the manager. In windows I could create a shortcut to open each profile. How do I do the same thing with ubu?

---

### Post by smsmith on 2009-08-20
Make a launcher like you normally would, and at the end, try one of the following:

**-P "profile name"**

or

**-profilemanager "profile name"**

"profile name" is the name of the profile as it is listed in the profile manager window.

Your launcher path *might* look like this:

firefox -P "profile 1"  <-- if the profile was named **profile 1**

---

### Post by mercules2178 on 2009-08-20
no luck, it did not work on any of the profiles, any other suggestions?

---

### Post by mercules2178 on 2009-08-20
scratch that, works as a launcher but not as a desktop icon, each icon will overwrite the current icon on the desktop. Any way around that?

---

