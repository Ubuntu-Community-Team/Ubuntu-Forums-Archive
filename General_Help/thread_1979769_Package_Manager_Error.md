---
title: "Package Manager Error"
date: 2012-05-14
forum: General Help
---

### Post by ed4sdr on 2012-05-14
I am using Ubnuntu 11.04 on standalone PC.
The system denies to add any pkg installation and prompt to run Package Manager (not possible as the PC is standalone!) because of "Error: BrokenCount>0"

Package Catalogue repair screen appears
 
How can i resolve this issue?

Thnx in adv.

Regards

---

### Post by plucky on 2012-05-14
> **ed4sdr said:**
> I am using Ubnuntu 11.04 on standalone PC.
The system denies to add any pkg installation and prompt to run Package Manager (not possible as the PC is standalone!) because of "Error: BrokenCount>0"

Package Catalogue repair screen appears
 
How can i resolve this issue?

Thnx in adv.

Regards

Open a terminal (CTRL+ALT+T) and post the output for ```
sudo apt-get update && sudo apt-get upgrade
```

So we can see what is causing the "Error: BrokenCount>0"

Good Luck

---

### Post by ed4sdr on 2012-05-16
Although, apt-get update cant work for me since internet connection not available but following has worked for me when apt-get install -f failed to resolve the issue;

sudo rm /var/lib/apt/lists/* -vf

Thanks for your time :)

---

