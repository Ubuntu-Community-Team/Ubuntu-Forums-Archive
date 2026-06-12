---
title: "Lirc Controls Both MythTV and VLC at the same time"
date: 2010-03-19
forum: General Help
---

### Post by psylencer on 2010-03-19
Hi all

I have no problems getting LIRC to work with both Mythfrontend and VLC, However both are controlled at the same time.  Is there any way to prevent this from happening so that LIRC controls only the program "on top" (VLC) while having no effect on the program underneath (mythTV).

Any help greatly appreciated. 

Thanks

---

### Post by psylencer on 2010-03-20
bump: anyone?

---

### Post by Flaming_Amarant on 2010-04-01
I don't use VLC to watch my videos so I do not have that problem. Anyway I use mplayer, and works just fine. So when you are watching your video and you press a button, what happens exactly?

---

### Post by psylencer on 2011-07-23
Turned out to be an issue with LIRC itself.  Does not have the capacity to only issue instructions to the current window with programs with in built lirc support.  I had to use irxevent and manually configure my mappings to get this to "work".

Thanks for your help though.

---

