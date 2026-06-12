---
title: "speakers not disabled using headphones"
date: 2011-05-13
forum: General Help
---

### Post by Slim11208 on 2011-05-13
Hello, 

About 3 days ago I installed Ubuntu 11.04 on my HP Pavilion dv7 CTO Notebook. 

I just noticed that when I plug in my headphones the speakers still play. I checked System / Sound  and there is no option to correct the issue. 

It's not a hardware failure as it does not happen in Windows 7

---

### Post by smithark on 2011-05-13
try this:

> In sound preferences, go to the output tab and change connector to Analog Headphones.

Now use alsamixer from terminal and increase Headphone and PCM to 100%, and mute Front with m (if not muted already). Changing Master Front and the muted Front, while leaving muted change the volume. 

Note: If I move Master Front above appr. 70% I have a constant noise from my headphone, in that case lower Master Front, and increase Front's volume.

this worked for me. took from another thread. credit goes to the orgl author.

---

### Post by Slim11208 on 2011-05-13
> **smithark said:**
> In sound preferences, go to the output tab and change connector to Analog Headphones.
.

Thank you, but I do not get "analog headphones" as an option. I have Analog Speakers and Analog Output. 

note: when using Analog Output I don't get any sound at all.

---

