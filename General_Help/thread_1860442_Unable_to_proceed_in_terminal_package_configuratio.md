---
title: "Unable to proceed in terminal package configuration prompt"
date: 2011-10-14
forum: General Help
---

### Post by goodmorningcaptain on 2011-10-14
Because at [this]("http://img254.imageshack.us/img254/8685/screenshotob.png") screen, I can't figure out for the life of me how to select "<Ok>".

Normally (for me) in this sort of terminal prompt the options are already selected and all I need to do is press enter... can anyone tell me what the problem is? 

Thanks.

---

### Post by spiky001 on 2011-10-14
Have you tried he down arrow key or the TAB key

---

### Post by goodmorningcaptain on 2011-10-14
Tab worked; thank you.

---

### Post by dcstar on 2011-10-14
> **goodmorningcaptain said:**
> Because at [this]("http://img254.imageshack.us/img254/8685/screenshotob.png") screen, I can't figure out for the life of me how to select "<Ok>".

Normally (for me) in this sort of terminal prompt the options are already selected and all I need to do is press enter... can anyone tell me what the problem is? 

Thanks.

```
sudo dpkg-reconfigure debconf
``` and selecting "Gnome" will fix these in the future.

---

