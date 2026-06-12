---
title: "Restarting an update that hung..."
date: 2011-07-30
forum: General Help
---

### Post by CoolBreeze47 on 2011-07-30
Hi everyone

When I did a very large update earlier (about 100 package updates for the new KDE 4.7) it hung at 88%. After waiting for over an hour, I just decided to reboot. After rebooting, I was surprised to see that many of the updates (and new features) had been installed, however, just to be sure, is there a way to use apt-get to "resume" where I left off before it hung up?. All of the updates had already been downloaded, prepared, etc. It was during the actual installation process that it hung up. Refreshing the package list shows no packages that need updating (same result by using apt-get). I simply want to resume where I left off.

Thanks so much!

---

### Post by jerrrys on 2011-07-30
this has happen to me a couple of times in the pass.  come to find out that the install was completed,  it was just the install screen that got hung up.

in my case, after giving it an hour or so to complete.  i just closed it out.  and then to my surprise it said something like restart needed and i was good to go.

kde is setup different, but wonder if this happen to you

---

### Post by ankspo71 on 2011-07-31
Hi,
If you interrupted an update it could prevent you from installing anything else. If you can't install anything, try opening a terminal and pasting this command into it:
```
sudo apt-get install -f
```
If all goes well it will continue updating the system (if needed).

Hope this helps.

---

