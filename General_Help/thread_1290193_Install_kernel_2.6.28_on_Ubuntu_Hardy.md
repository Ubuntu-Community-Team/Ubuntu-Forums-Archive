---
title: "Install kernel 2.6.28 on Ubuntu Hardy"
date: 2009-10-13
forum: General Help
---

### Post by Ang89 on 2009-10-13
The latest kernel available on hardy's repository is 2.6.24, but I need 2.6.28 in order to get my USB modem working. Well, I want to switch my repository to jaunty's and install the latest kernel, but is it save to do so?

---

### Post by Arup on 2009-10-13
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28/)

You are going to loose all the prorietary drivers including video, wireless etc. and you would have to compile your own video drivers.

---

### Post by Ang89 on 2009-10-13
> **Arup said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.28/)

You are going to loose all the prorietary drivers including video, wireless etc. and you would have to compile your own video drivers.

Sounds terrible. I think I'll just wait til karmic then . .

---

### Post by justleen on 2009-10-13
It isn't that bad, since you can get the config of your current running kernel from /boot/ and do a make oldconfig ...

---

### Post by nikhilbhardwaj on 2009-10-13
its a little difficult to compile the kernel for the first time
but if you stick through it's very rewarding

---

