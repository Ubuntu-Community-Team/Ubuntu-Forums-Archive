---
title: "Hang ups"
date: 2010-01-29
forum: General Help
---

### Post by Namesake on 2010-01-29
Hey all,

I have Ubuntu 9.10 on my dell xps 1330m laptop. I upgrade from Jaunty. I have been running this os for roughly 3 months and have had no problems. But lately my laptop has been hanging, making me resort to a forced shutdown (holding down the power button).

Does any one know the source of this?

Many thanks
:p

---

### Post by lidex on 2010-01-29
> **Namesake said:**
> 

Does any one know the source of this?

:p

Not without more information. Is the whole system freezing and when does it occur? Does it happen randomly or when you run a specific program? Have you noticed any other glitches in graphics or touchpad? Have you tried disabling "Visual Effects"?

Look in your "~/.xsession-errors" file and "/var/log/messages" for clues. I'm not sure about "/var/log/dmesg", but you can check it also - look near the end. If you post any output here, please use the code tags.

---

