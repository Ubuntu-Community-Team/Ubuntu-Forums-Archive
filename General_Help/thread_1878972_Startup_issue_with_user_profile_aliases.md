---
title: "Startup issue with user profile aliases"
date: 2011-11-10
forum: General Help
---

### Post by srosro on 2011-11-10
I recently added a startup script with the following command:

sudo update-rc.d startup_script defaults 99

however the script refers to a few aliases that are in my .profile and also use my public key to check out a git repository.  Neither work.  I've moved the aliases to /etc/profile but no avail. 

startup_script works fine once I log in.

I'm at a loss as to how I can make these aliases and the public key available during bootup.  Any ideas?

---

