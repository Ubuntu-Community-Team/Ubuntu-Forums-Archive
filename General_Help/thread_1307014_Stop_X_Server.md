---
title: "Stop X Server"
date: 2009-10-30
forum: General Help
---

### Post by jsc_moraga on 2009-10-30
Oy. Is it me or is Ubuntu getting harder to use and not easier?

I want to stop the X server, so I can install the Nvidia drivers by hand. However, the regular way of doing that, dropping to a terminal and /etc/init.d/gdm stop doesn't work anymore. WTF?

Can someone please explain how to do stop the x server?

This thread addressed the subject, but no resolution: [http://ubuntuforums.org/showthread.php?t=546421&page=2](http://ubuntuforums.org/showthread.php?t=546421&page=2)

And the post was filled with people asking why someone would want to do that. Please don't ask that, as I have my reasons and that's enough. 

Developers: If you going to change the behavior of something this radically, please explain the new method of doing it.

Thanks,

jsc

---

### Post by JBAlaska on 2009-10-30
You gotta sudo it;
```
sudo /etc/init.d/gdm stop
```

---

### Post by jsc_moraga on 2009-10-30
Sorry, I did that. I forgot to put it in the post. So even with sudo it doesn't work.

jsc

---

### Post by JBAlaska on 2009-10-30
Huh, I have no idea why not, on 9.10 it works just fine for me.

Edit: I just tried it on my Hardy box and it worked there 2 (I knew it would...but just for the halibut I tried it).

---

### Post by happyhamster on 2009-10-30
Try:

sudo service gdm stop

sudo service gdm start

---

### Post by jsc_moraga on 2009-10-30
Thank you very much. Worked fine.

Is there a man page for "service"?

jsc

---

### Post by happyhamster on 2009-10-30
It's provided by the package "sysvinit-utils" I think, and there should be a rudimentary "man service" page. Good luck.

---

