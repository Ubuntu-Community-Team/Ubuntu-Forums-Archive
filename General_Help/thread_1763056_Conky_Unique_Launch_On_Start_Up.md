---
title: "Conky Unique Launch On Start Up"
date: 2011-05-19
forum: General Help
---

### Post by S_Papadakis on 2011-05-19
Greetings Boys and Girls.

I started using Ubuntu with no previous knowledge of linux, a year ago. I've been solving all my problems through trial & error (a few fresh installs, too...) but I think I'm going to need help on this one. 

Just started playing around with Conky in 10.10 and it's running just great, I just can't figure out how to get it running on start-up. I know I'll need to write a script and I've read through quite a few forums, however for me to start Conky, I need to use a unique terminal launch:

$ Conny -c ~/.conky/conkyrc_HUD

I'm not sure how to quite do it and I would usually just do trial & error, but since this is a start script, I'd rather just get done right the first time.

Thanks in advance for any help.

---

### Post by hopelessone on 2011-05-19
Menu >> Preferences >> Startup Applications

---

### Post by S_Papadakis on 2011-05-19
Already, tried that, but since it is a unique launch, it only starts up the generic black & white conky.

---

### Post by hopelessone on 2011-05-19
try adding a short delay in the startup file:
```
#! /bin/bash/
sleep 6
/usr/bin/conky
```

---

### Post by wojox on 2011-05-19
Put this in gedit and save it as .conky_start

```
#!/bin/bash
sleep 10 &&
conky -c ~/.conky/conkyrc_HUD &
```

Right click and make it executable and add it to start up.

---

### Post by S_Papadakis on 2011-05-19
Thanks, will do.

---

### Post by S_Papadakis on 2011-05-19
Thanks again. Haven't had to write a script up until now and I just realized how simple my problem is. D'oh.

---

