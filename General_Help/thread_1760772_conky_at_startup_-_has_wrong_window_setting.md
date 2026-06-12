---
title: "conky at startup - has wrong window setting"
date: 2011-05-17
forum: General Help
---

### Post by BravoDelta65 on 2011-05-17
I have conky running a simple script on my Ubuntu 11.04 install. 

Running conky from using ALT-F2 is fine, but I have have conky added to the startup list, and when it runs from this, the conky window is different (ie not integrated with desktop layer). It has some shadowing around the edge and it seems to be on a layer other than the desktop. In addition to this, it stops running after a short while. I then run conky from ALT-F2 again and it's appears as I want, and stays there all day.

I have included what I think is the relevant code below from my conkyrc.

Has anyone had similar issues with a suitable way to resolve the problem?


```

own_window yes
own_window_transparent yes
own_window_type override
#own_window_type desktop
#own_window_type normal
#
own_window_type conky
own_window_class Conky

```

---

### Post by Stephen Morgan on 2011-05-17
That's because conky is starting before compiz, I had the same problem, you need to put a script in the start-up programmes, rather than conky itself, and have the script delay for ten seconds or so before starting conky.

---

