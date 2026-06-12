---
title: "How to copy user / profile settings"
date: 2010-08-20
forum: General Help
---

### Post by Rebelli0us on 2010-08-20
How do I transfer my user profile and settings to a new user?

I copied over Theme files for "Appearance". But I also need to copy (taskbar) Panels and keyboard shortcuts.

Are there files I can simply copy to the new profile? I'm grateful there is NO "registry" in Linux, or is there?

---

### Post by Vaphell on 2010-08-20
all your profile configuration is in so called dotfiles - files/directories with names starting with a dot. You got plenty of them in your home directory

to see them: ctrl+h in nautilus or ls -la .* in terminal

once you copy them over as a root, set the ownership with chown command - usually you cannot use another user's files

sudo chown -R newowner:newowner <files/dirs>


```
sudo find ~newowner -maxdepth 1 -name ".*" -exec chown -R newowner:newowner {} \;
```
should set the ownership

---

### Post by Rebelli0us on 2010-08-20
Thank you. So where are the Panels and keyboard shortcuts? There's a directory named .config, can I copy over the whole thing?

---

