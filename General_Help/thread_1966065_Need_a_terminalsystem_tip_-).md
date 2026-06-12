---
title: "Need a terminal/system tip :-)"
date: 2012-04-26
forum: General Help
---

### Post by epos85 on 2012-04-26
Hi!

Ive just installed 12.04 and think its a bit slow. Tried to execute the comand below in terminal, and I think its working.
```
ROOT$ echo N> /sys/module/drm_kms_helper/parameters/poll
```

I found the command in a fedora forum, but they told us to use the command under if we want it to be executed at boot.
```
ROOT$ echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf
```

Does this also work in ubuntu? Where can I put the command/script? Please supply both options ;-)

Are there any other ways to speed up 12.04? I cant remember last time this laptop beeing so slow.. Ubuntu 10.04 and 11.04 was much faster. Even vista was faster :o


Thanks for any reply.. 
And sorry for my english, im a bit tired xD

---

### Post by CharlesA on 2012-04-26
I don't know what the drm_kms_healer object does, but read this:
[http://askubuntu.com/questions/21666/can-turning-off-drm-kms-helper-polling-affect-screen-brightness-control](http://askubuntu.com/questions/21666/can-turning-off-drm-kms-helper-polling-affect-screen-brightness-control)

---

