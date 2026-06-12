---
title: "The following packages have been kept back:   xbmc xbmc-bin"
date: 2011-04-20
forum: General Help
---

### Post by kyutums on 2011-04-20
I tried updating my packages via "sudo apt-get upgrade". Almost everything got updated, except for XBMC. I received the following message:
> The following packages have been kept back:   xbmc xbmc-bin

I tried
> sudo add-apt-repository ppa:nvidia-vdpau
but I still got the same result.

Any ideas on how to upgrade XBMC?

---

### Post by ttshivers on 2011-04-20
Run this in the terminal
```
sudo apt-get dist-upgrade
```

---

### Post by kyutums on 2011-04-20
That did it. Thanks! :)

---

