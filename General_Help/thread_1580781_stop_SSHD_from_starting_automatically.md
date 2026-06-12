---
title: "stop SSHD from starting automatically"
date: 2010-09-23
forum: General Help
---

### Post by vincix on 2010-09-23
I've installed openssh-server on my ubuntu netbook, and now I am trying to stop it from starting by itself. I can stop it temporarily, but whenever I restart my computer, it starts again. I've tried rcconf and chkconfig but none of them recognises it as open. Any help?

---

### Post by IcewindDale on 2010-09-24
Hi.
If you find you have no further use for it might be best to uninstall it completely.

If you need to use it sometimes, please check the following thread [http://ubuntuforums.org/showthread.php?t=1521135](http://ubuntuforums.org/showthread.php?t=1521135)

I thought this could be quite simply handled by update-rc.d but while testing it myself the daemon kept starting on boot and I can't figure out any other way besides the one on that thread.

---

### Post by vincix on 2010-09-24
Thanks for such a prompt answer :) 
I did find the solution on your link. It seems that Ubuntu doesn't offer a user-friendly option to prevent sshd from starting automatically. I find it a little strange.

---

### Post by SlugSlug on 2010-09-24
```
sudo update-rc.d -f ssh remove
```



ahh just read second thread -- does this not work?

---

### Post by vincix on 2010-09-24
Well, it didn't work there, so I really haven't tried it either. But writing that do_not_run script in /etc/ssh did the trick. It's just a little strange how ubuntu chose to give this roundabout solution or rather let the user figure it out by themselves - I guess this solution would work on any other distribution, after all.

---

### Post by IcewindDale on 2010-09-24
> **SlugSlug said:**
> ahh just read second thread -- does this not work?

I thought it would too, but then I tried it on a VM I keep for testing purposes and for some reason the daemon kept launching on boot and I had no idea why. Then I found that thread and apparently it's method works, albeit not exactly a simple method, so I didn't search any further.

---

