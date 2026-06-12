---
title: "Google Chrome needs cache clearing to use it!"
date: 2010-02-27
forum: General Help
---

### Post by Jose Catre-Vandis on 2010-02-27
Trying out Google Chrome.

Have found that in order to get it to load pages I need to completely clear "Everything" from the cache, and then restart before it will work, and then on the next reboot do the same thing again. Amnd even then sometimes it doesn't work.

Any clues

(Xubuntu 9.10)

---

### Post by kerry_s on 2010-02-27
thats weird, what chrome version? are you using a proxy?
i'm using 5.0.335.0 dev

---

### Post by Jose Catre-Vandis on 2010-02-27
5.0.307.9 beta

Not using a proxy

Will load [www.google.co.uk](www.google.co.uk) as the home / start page, but times out on all other pages offering Wait or Kill

---

### Post by Stovey on 2010-02-27
I love Google Chrome.

5.0.307.11.

No problems with pages loading (or anything else).

Ubuntu 9.10.  Acer Aspire One Netbook.

---

### Post by kerry_s on 2010-02-27
you guys do know that dev has the new features every 1's been waiting for?

---

### Post by Jose Catre-Vandis on 2010-02-28
> **kerry_s said:**
> you guys do know that dev has the new features every 1's been waiting for?

OK, help please with getting on to the dev version. Is there an SVN somewhere for this?

---

### Post by kerry_s on 2010-02-28
this is the repo i'm using:
```
deb http://dl.google.com/linux/deb/ stable non-free main
```

it will show both beta & dev

---

### Post by Jose Catre-Vandis on 2010-02-28
Well, tried the dev version (thanks for the repo kerry_s).

Still got the same problem (even after deleting ~/.config/google-chrome). Will load homepage ([www.google.co.uk](www.google.co.uk)) but no other "complex" pages like this forum.

---

### Post by Jose Catre-Vandis on 2010-02-28
Additional:

Seen another thread where KDE users having the same problem.

can get pages to load if I disable plugins:
```
google-chrome --disable-plugins
``` but the will give reduced functionality.

Also notice that if I run from the terminal I get this error:
```
[4871:4871:15335111704:ERROR:/usr/local/google/b/slave/chrome-official-linux/build/src/chrome/browser/process_singleton_linux.cc(313)] Failed to extract pid from path: /home/jose/.config/google-chrome/SingletonLock
```

---

### Post by Richard1979 on 2010-02-28
Not to be rude but what's wrong with just using Firefox?
If you need to run Chrome to test websites then you can easily run Windows in Virtualbox?

---

### Post by 98cwitr on 2010-02-28
im on 5.0.307.9 beta and never had that problem. I did have that occur once on my windows machine.

---

### Post by Jose Catre-Vandis on 2010-02-28
> **Richard1979 said:**
> Not to be rude but what's wrong with just using Firefox?
If you need to run Chrome to test websites then you can easily run Windows in Virtualbox?

It's a matter of it's there, so lets make it work

---

