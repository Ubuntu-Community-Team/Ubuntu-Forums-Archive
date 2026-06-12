---
title: "How do you edit apt to never upgrade a package?"
date: 2006-05-12
forum: General Help
---

### Post by mandrakethepenguin on 2006-05-12
I compiled lighttpd myself, because I dont like the version on the repos.  But, apt keeps bugging me and asks me to upgrade. How do I omit lighttpd in apt's upgrade process?

---

### Post by tonyr on 2006-05-12
What you want to do is called **apt pinning**.   I haven't figured it out,
but some people have.  Start with **man apt_preferences**. The file it
talks about, **/etc/apt/preferences**, does not seem to exist by default, so 
you'd have to create it.

There is a Beginner's Guide at [URL="http://jaqque.sbih.org/kplug/apt-pinning.html"]
http://jaqque.sbih.org/kplug/apt-pinning.html[/URL].  
You should search the forums for (or google for) **apt pinning**.

---

### Post by aysiu on 2006-05-12
This can be done in Synaptic Package Manager as well--see attached screenshot.

---

### Post by tonyr on 2006-05-13
[QUOTE=aysiu]This can be done in Synaptic Package Manager as well--see attached screenshot.[/QUOTE]

Thanks for the pointer.  I'm still learning.   Synaptic doesn't use **/etc/apt/preferences**,
apparently, but it's own **/var/lib/synaptic/preferences**.  Maybe it would
use **/etc/apt/preferences** if it existed, I don't know. The entry it
created for me when I **Locked** my **wifi-radar** package is
```

Package: wifi-radar
Pin: version 1.9.6-0ubuntu4
Pin-Priority: 1001

```

So I'm guessing that a similar entry in **/etc/apt/preferences** should work
for **apt-get**, **aptitude**, and **adept** (only a guess).

---

