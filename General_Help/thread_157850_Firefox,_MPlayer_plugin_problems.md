---
title: "Firefox, MPlayer plugin problems"
date: 2006-04-10
forum: General Help
---

### Post by keithg on 2006-04-10
I have installed MPlayer, the essentials, the fonts, and mozilla-firefox plugin using synaptic packet manager.  I have no problems with those, but I do have a problem with getting it set as the default for the different file types in Edit>Preferences>Downloads.  In the filetypes box there is no list of filetypes.

I am not sure how to fix my problem, but I would appreciate it if someone happens to know.  :) 

thank you,
Keith

---

### Post by aysiu on 2006-04-10
If you remove the Totem plugins, MPlayer should be the default. ```
sudo rm /usr/lib/mozilla-firefox/totem*
```

---

