---
title: "resolution won't 'stick'"
date: 2006-06-13
forum: General Help
---

### Post by jmacak on 2006-06-13
Hi

I am having trouble convincing (k)ubuntu to keep the resolution that I choose (1280x1080), it prefers 600x800.  Everytime I re-start my machine, it goes back to 600x800 and I go into system settings/display and re-set it to 1280x1080.

I went through dpkg-reconfigure xserver-org, answered the questions as best I could and even picked 1280x1080 as my resolution, but, after re-starting, back it was at 600x800.

I should mention that I have upgraded my monitor (syncmaster 930b), my previous one probably could not support much over 600x800.

Anyone have any ideas on what I'm doing wrong?

thanks

joe in seattle

---

### Post by caserio on 2006-06-13
Hi,

Backup your /etc/X11/xorg.conf first then delete the "800x600" res for each entry (Depth) in the Section "Screen".

---

### Post by jmacak on 2006-06-13
Hi Caserio

Thanks for the suggestion.  I removed the "600 x 800"s from the config file, restarted my machine, and lo and behold, 1280 x 1024.

Thanks for the help.

cheers

joe in seattle

---

