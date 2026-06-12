---
title: "screen saver turned on during updates, now cant update"
date: 2012-03-30
forum: General Help
---

### Post by 18rmiller on 2012-03-30
title pretty much says it. My laptop had not been turned on for a few days so when I did turn it on I had a lot of updates to do. During the update my screensaver turned on and when i put in my PW to turn it back on I got a message that the updates failed "please check your internet connection" well my internet works fine but no matter what i try I get the same message

11.04 BTW

---

### Post by kazztan0325 on 2012-03-30
Hi 18rmiller,

I think you have to reboot your PC with recovery mode, and run following command.

```
sudo dpkg --configure -a
```

---

