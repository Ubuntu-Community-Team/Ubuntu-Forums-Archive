---
title: "Update Mozilla Plugin via command line"
date: 2011-04-27
forum: General Help
---

### Post by tygsxr on 2011-04-27
Hi when going to mozilla add-ons(plugin section) i try to update and it tells me to update my version of shockwave flash 10.1 r999 when i do this it takes me to the adobe page which asks which version to download ive tried all options here but none seem to update. Does anyone no how i can update this to the new version 10.2 via command line, Thanks

---

### Post by user1397 on 2011-04-27
> **tygsxr said:**
> Hi when going to mozilla add-ons(plugin section) i try to update and it tells me to update my version of shockwave flash 10.1 r999 when i do this it takes me to the adobe page which asks which version to download ive tried all options here but none seem to update. Does anyone no how i can update this to the new version 10.2 via command line, Thanks
new releases of the flash plugin on ubuntu should come as an update in your update manager.  it usually takes a bit longer for it to show up than the day it's released on the website

---

### Post by tygsxr on 2011-04-27
Thanks for the quick reply. The only reason i am trying to update it is because i cannot view some streaming videos on line when i navigate to their pages the player will come up greyed out or black. The part that annoys me is that it has only just happening about two weeks ago.. Have you got any other suggestions.. Cheers

---

### Post by user1397 on 2011-04-27
> **tygsxr said:**
> Thanks for the quick reply. The only reason i am trying to update it is because i cannot view some streaming videos on line when i navigate to their pages the player will come up greyed out or black. The part that annoys me is that it has only just happening about two weeks ago.. Have you got any other suggestions.. Cheershave you installed the ubuntu-restricted-extras package?

---

### Post by gandaran on 2011-04-27
> **tygsxr said:**
> Hi when going to mozilla add-ons(plugin section) i try to update and it tells me to update my version of shockwave flash 10.1 r999 when i do this it takes me to the adobe page which asks which version to download ive tried all options here but none seem to update. Does anyone no how i can update this to the new version 10.2 via command line, Thanks
you should always install flash from the software package manager, this will keep it updated automatically when you install the system updates.
try to remember how you installed the flash 10.1 r999 and remove it first as installing another flash package wont remove it then install either the **ubuntu-restricted-extras** package or just the flash **flashplugin-installer** package.
do this only if your ubuntu system is 32-bits, if 64-bits post here again for instructions.
or use the firefox [flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") addon to fix it for both 32-bits and 64-bits

---

### Post by tygsxr on 2011-04-29
Thanks for the replies. I did need to uninstall flash and reinstall the new 10.2 version. i did via terminal. This works perfectly. The code is 

**sudo apt-get remove gnash && sudo apt-get install flashplugin-installer**

---

