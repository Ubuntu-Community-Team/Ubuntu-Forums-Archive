---
title: "Fully uninstall Chromium-Browser?"
date: 2012-08-10
forum: General Help
---

### Post by fixles on 2012-08-10
Hi,

Chromium just locked up my machine and I had to hold the power button and restart. When I opened chromium again it said it was unable to find my new tab extension. I clicked extensions and it froze again but I was able to force quit.

So I apt-get purge chromium-browser and re-install with apt-get install chromium-browser.

When I opened it I get the same error and the same freeze when I click extensions.

Evidently chromium hasn't fully un-installed as it should have asked me to login and re downloaded my bookmarks and extensions hopefully solving my problem.

There doesn't appear to be any files related to chromium in my home directory so how do I full purge chromium?

Thanks.

---

### Post by vasa1 on 2012-08-10
Look for a **hidden** folder called .**config** in your home folder. Inside that folder, look for for anything with **chromium** in the title. I don't use Chromium. I use Chrome. To be sure, this folder should have a subfolder called **Default**.

Rename the "chromium" folder to back it up thereby making it invisible to the browser or just delete it.

---

### Post by fixles on 2012-08-10
> **vasa1 said:**
> Look for a **hidden** folder called .**config** in your home folder. Inside that folder, look for for anything with **chromium** in the title. I don't use Chromium. I use Chrome. To be sure, this folder should have a subfolder called **Default**.

Rename the "chromium" folder to back it up thereby making it invisible to the browser or just delete it.

Thanks I uninstalled, deleted that folder and when I reinstalled it downloaded everything again solving the problem

---

