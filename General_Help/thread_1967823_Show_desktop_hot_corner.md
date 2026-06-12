---
title: "Show desktop hot corner"
date: 2012-04-28
forum: General Help
---

### Post by troysos on 2012-04-28
I just installed 12.04 and I love almost everything about it. I would really like a "show desktop hot spot" in the lower right corner. If I could just move my courser to the lower right and not click anything it would make my day.
Also, the scroll bars are so hard to see. When I more over to scroll I have to look to find where the small bar is. How can I fix that too? Thank you.

This is for 12.04 running Unity.

---

### Post by troysos on 2012-05-04
A lot of people have looked at this but I guess it can't be done?

---

### Post by MonkeyPaw on 2012-05-04
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

That will get you "Show Desktop" and Expose-like "Show all running" hot-corners. It can be a little buggy if your graphics aren't great. I think it requires 3D capability.

Not sure on the scroll bars. Never tried to change them.

---

### Post by troysos on 2012-05-04
Are you kidding me!! This Ubuntu tweak kicks ***! Why haven't I heard of this before. This tool does so much stuff. Thank you so much :)

---

### Post by MonkeyPaw on 2012-05-04
You're welcome. Like I said, it can be a little buggy. Especially window transparency. Occasionally it makes them non-responsive.

---

### Post by ryanyeah on 2012-05-04
I'd say it's easier to just go compiz settings manager. Then just go to compizconfig > general options >key bindings and choose where you want the show desktop to appear.

---

### Post by pqwoerituytrueiwoq on 2012-05-04
you can go into ccsm (compizconfig settings manager) and set multiple corners/edges
it is in the expo plugin

---

### Post by ryanyeah on 2012-05-04
> **pqwoerituytrueiwoq said:**
> you can go into ccsm (compizconfig settings manager) and set multiple corners/edges
it is in the expo plugin

Yes... although the screenshot is going to be outdated as OP is running 12.04.

---

### Post by pqwoerituytrueiwoq on 2012-05-04
it is close enough for what it is for but i am using 12.04
```
chad@chad-cq60-215dx:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
chad@chad-cq60-215dx:~$ compiz --version
compiz 0.8.4
chad@chad-cq60-215dx:~$
```
i took compiz from lmde due to a few bugs in the current version

---

### Post by troysos on 2012-05-06
Every time I shut my computer down then restart I have to go back into Ubuntu Tweak and redo those settings, then it works. How do I keep the Ubuntu Tweak settings even after I restart my computer?

---

### Post by MitraX on 2012-07-04
> **troysos said:**
> Every time I shut my computer down then restart I have to go back into Ubuntu Tweak and redo those settings, then it works. How do I keep the Ubuntu Tweak settings even after I restart my computer?

It seems that unityshell plugin is rewritting the expo plugin configuration.

Here is the solution that works for me: [http://www.inforbiro.com/blog-eng/ubuntu-12-04-hot-corner-stop-working/]("http://www.inforbiro.com/blog-eng/ubuntu-12-04-hot-corner-stop-working/")

---

