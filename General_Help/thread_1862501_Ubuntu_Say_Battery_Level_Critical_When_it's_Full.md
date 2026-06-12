---
title: "Ubuntu Say Battery Level Critical When it's Full"
date: 2011-10-16
forum: General Help
---

### Post by Simeo on 2011-10-16
This is a new issue that "developed" with the install of 11.10. My battery has no issues, but when I unplug the computer immediately Ubuntu says the battery level is critical and hibernates. 

I tried changing the power settings as a workaround but there are only two options in the power menu when "battery is critical": Hibernate and Shutdown

This is really annoying...help?

---

### Post by Simeo on 2011-10-17
Bump. 

Ubuntu shuts my computer down on full battery when I unplug and I can't disable the feature. Please help.

---

### Post by malc234 on 2011-10-17
Hey, i'm having the same problem. With the previous releases I was able to open a terminal window, type gconf-editor, click the apps tab, scroll down to gnome power manager, click actions, right click the critical battery key and select edit key. Then change it to 'nothing'. 

This no longer works for me but may work for you. Hope this helps.

---

### Post by Simeo on 2011-10-17
> **malc234 said:**
> Hey, i'm having the same problem. With the previous releases I was able to open a terminal window, type gconf-editor, click the apps tab, scroll down to gnome power manager, click actions, right click the critical battery key and select edit key. Then change it to 'nothing'. 

This no longer works for me but may work for you. Hope this helps.

In 11.10 I know we have dconf-editor now... but I tried going to it like you said and the option doesn't exist...

---

### Post by Simeo on 2011-10-18
Bump?

---

### Post by malc234 on 2011-10-18
I had to manually install dconf-editor, but yeah your right,  there's no option for the gnome power manager as you said. I'm still very much a novice so i'm all out of ideas. 

This battery issue is the only problem i'm having with 11.10. So frustrating.

---

### Post by Simeo on 2011-10-19
Issue just fixed itself today on last update. Sweet.

---

