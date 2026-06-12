---
title: "tar backup permissions"
date: 2010-05-17
forum: General Help
---

### Post by stevepoppers on 2010-05-17
I'm working out my backup process. I'm getting the hang of tar, but I notice a few errors relating to permissions. It can't copy /etc/passwd, /etc/shadow, etc. Should these be backed up? Is it dangerous? Do I need them if/when I move/restore the /home and /etc folders?

---

### Post by bb002 on 2010-05-17
Those files contain all the usernames/password combos that exist on your system. This includes system accounts.

I believe the preferred practice is to no backup/restore those files along with /etc/groups. In general I don't think it is wise to blindly restore /etc. Backing it up is fine but restore only the files you need if you need them. Blindly restoring all of /etc is like backing up the registry in windows then restoring sometime in future. Who knows what just went boom when you do that, haha.

I normally recreate the users manually or with a script for large user restores. then chown the /home directories back to their proper user.

---

### Post by stevepoppers on 2010-05-17
That makes sense. So, I re/install, create my user, and that creates these directories for that install. Glad to know I don't have to worry about it.

I'm trying to back up as much as I can of my settings and configuration. I only have one user on my laptop and probably only ever will. Looking at the FSH, it seemed that there would be a lot of my configuration in /etc.

---

