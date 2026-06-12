---
title: "Don't have System -&gt; Preferences -&gt; Display"
date: 2010-09-14
forum: General Help
---

### Post by gontz on 2010-09-14
I would like to change the resolution of my screen but I don't have the **Display** menu item under **System** -> **Preferences**.

I am currently running  Ubuntu 10.04 LTS  - the Lucid Lynx but Display was also missing before I upgraded from either 9.04 or 9.10 (I'm not sure which it was) so this issue is not exclusive to 10.04.

---

### Post by pcdave98 on 2010-09-14
system>pref>monitors

---

### Post by Viaxl on 2010-09-14
if you got a nVidia driver installed you should go to
```
sudo nvidia-settings
```
to adjust your display

maybe it's not the issue, just some suggestion

---

### Post by howefield on 2010-09-14
> **Viaxl said:**
> if you got a nVidia driver installed you should go to
```
sudo nvidia-settings
```

Or maybe even

```
gksudo nvidia-settings
```

---

### Post by gontz on 2010-09-14
system>pref>monitors is what I was looking for! I honestly didn't even see **Monitors** because my brain was so fixed on finding **Displays** or something that said **Resolution**.

I feel foolish now.

Thank you! 

This issue is resolved.

---

### Post by SnoepDogg on 2011-01-22
Yes, but the new "monitors" one only sets a couple basic monitor parameters. The older "Display" allowed me to configure many, many things about the X-Server as well as getting info from the GPU. 
Now, with 10.10 I'm having the "popular" x-server failure and I've tried several command-line fixes suggested on the few threads pertaining to meerkat bugs, all to no avail . Plus, the threads pertain specifically to Nvidia issues, and mine is an old Riva TNT-2 video card, which works perfectly with Ubuntu 9.10

---

