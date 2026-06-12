---
title: "No Volume After Boot"
date: 2011-02-03
forum: General Help
---

### Post by golfnut324 on 2011-02-03
I finally got the nerve to upgrade from 9.10 to 10.04. Got everything working except, when I boot, my speaker sound is all the way down. I run alsamixer from terminal, adjust speaker volume up and I'm ok until next boot. How do I set it to boot with speaker volume at last setting or all the way up?

Thanks.

---

### Post by wojox on 2011-02-03
After you run "alsamixer" run this and reboot:

```
sudo alsactl store
```

---

### Post by golfnut324 on 2011-02-03
> **wojox said:**
> After you run "alsamixer" run this and reboot:

```
sudo alsactl store
```



Ok, please go slow cause I'm still fairly new here. I ran "alsamixer" then adjusted the speaker volume up. Opened a second terminal and ran "sudo alsactl store". Rebooted and speaker output was still reset to 0.

Am I missing something?

Thanks for helping.

---

### Post by wojox on 2011-02-03
Don't know, I usually run alsamixer set it and close it and run sudo alsactl store

---

