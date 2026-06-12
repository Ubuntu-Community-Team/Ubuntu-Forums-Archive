---
title: "Damaged zeitgeist"
date: 2011-11-26
forum: General Help
---

### Post by Bliepo32 on 2011-11-26
Hey everyone,

I have a bit of a problem. I added the zeitgeist ppa to install activity-log-manager. It worked fine, untill there was an update for zeitgeist (from the ppa, wasn't paying attention). Off course, the update went wrong and I was told to execute the command 'sudo apt-get install -f'. So I did. I also removed the ppa. But the damage had already been done. I reinstalled zeitgeist, but unity won't search for apps, or anything at all for the matter.
Is there any way to fix this?

---

### Post by seiflotfy on 2011-11-28
can u run zg in a terminal and give me the output when u try a search

---

### Post by Bliepo32 on 2012-01-04
I have managed to fix the problem by removing and reinstalling the packages related to unity and zeitgeist. I am documenting it here in case someone else runs into the same problem. **Beware that I just tried some things and it worked. It is not some well thought-out process.** These were the commands I ran to fix it:
```

sudo apt-get autoremove unity-2d
sudo apt-get autoremove unity-2d-panel
sudo apt-get autoremove unity-2d-places
sudo apt-get autoremove unity-2d-launcher
sudo apt-get install unity-2d-launcher
sudo apt-get install unity-2d-places
sudo apt-get install unity-2d-panel
sudo apt-get install unity-2d
sudo apt-get install zeitgeist
sudo apt-get install zeitgeist-extension-fts
sudo apt-get install unity-lens-applications
sudo apt-get autoremove unity-common
sudo apt-get install unity-common
sudo apt-get check
sudo apt-get check unity-common
sudo apt-get autoremove zeitgeist-core
sudo apt-get install zeitgeist-core unity-lens-applications unity-lens-files zeitgeist zeitgeist-datahub zeitgeist-extension-fts
sudo apt-get install synapse
sudo apt-get auto-remove unity
sudo apt-get autoremove unity
sudo apt-get autoremove zeitgeist

```
After that I rebooted and things worked once again :)

---

