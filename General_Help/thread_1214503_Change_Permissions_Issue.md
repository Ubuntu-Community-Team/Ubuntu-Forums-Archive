---
title: "Change Permissions Issue"
date: 2009-07-16
forum: General Help
---

### Post by measekite on 2009-07-16
I am trying to change the Thunderbird Profile Folders permissions from root to username.

There are many nested files and subfolders.

I went to terminal and did a gksu nautilus and provided the proper password.  Root nautilus came up and I navigated to the correct folder.

I then changed the owner from root to username and did same for group.  I clicked on APPLY PERMISSIONS TO ENCLOSED FILES.

Only the folder I was working on got changed.  The subfolders remained as they were.  It appears that I have to change each one individually.

Is there a bug or is there something else to do?

---

### Post by Lasiaf on 2009-07-16
do this in terminal

sudo chown -hR username .mozilla-thunderbird

---

### Post by measekite on 2009-07-16
> **Lasiaf said:**
> do this in terminal

sudo chown -hR username .mozilla-thunderbird


Thanks:popcorn:

---

