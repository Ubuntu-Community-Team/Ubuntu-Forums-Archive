---
title: "Update manager got interupted, should I be concerned?"
date: 2010-08-29
forum: General Help
---

### Post by oxf on 2010-08-29
OK here's what happened...

I was was running Update Manager. All Downloads were completed and from what I could tell the Installations were about 75% complete. Then my PC suddenly went to suspend and I quickly entered password, at which point I got the message "you will need to restart your computer to continue installing updates"

So I did but after bootup there was no message about updates. I started Update Manager and after doing its scan informed there were no updates to install. Now it's possible that they did JUST finish installing went it suspended. However, I'm wondering if I might have still a few uninstalled updates lurking on my system? Is there anyway of checking this and should I be concerned??

Thanks

---

### Post by oxf on 2010-08-29
OK there are a bunch of folders in the tmp folder. If I boot up from cold and they are still there can I assume they were left over from the interrupted installation process?
If so how do I deal with them?

---

### Post by oxf on 2010-08-29
Can anyone advise me on this please?

---

### Post by helliewm on 2010-09-08
You could try sudo dpkg-reconfigure --a

Helen

---

### Post by JohnHeikkila on 2010-09-08
or "dpkg --configure -a" to configure whatever was left out

---

### Post by oxf on 2010-09-13
> **helliewm said:**
> You could try sudo dpkg-reconfigure --a

Helen

> **JohnHeikkila said:**
> or "dpkg --configure -a" to configure whatever was left out

OK thanks for that. I think I got it sorted anyway. But that's useful info and filed for future reference :)

---

