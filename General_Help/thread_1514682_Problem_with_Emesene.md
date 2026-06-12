---
title: "Problem with Emesene"
date: 2010-06-21
forum: General Help
---

### Post by NeverHide on 2010-06-21
Every time i start Emesene i get this message:

```

You are using emesene 1.6.1 "mate" so you're free to complain here:
http://forum.emesene.org/index.php/board,19.0.html
Check already existing tickets for duplicates first, please.
Traceback (most recent call last):

  File "/usr/share/emesene/emesenelib/soap/manager.py", line 139, in process
    return process()

  File "/usr/share/emesene/emesenelib/soap/manager.py", line 76, in process
    response.callback(response, *response.args)

  File "/usr/share/emesene/emesenelib/ProfileManager.py", line 152, in onGetProfile
    self.affinityCache = response.body.split('</CacheKey>')[0].split('<CacheKey>')[1]

IndexError: list index out of range


```


everything works ok but getting this message every time i start emesene is getting a bit annoying :mad:

Anyone has any ideas?

---

### Post by _Narcisse_ on 2010-06-28
Hello,

Emesene started doing this a few days ago. I got exactly the same error message. I'll do a few searches and let you know if I find any workaround.

Anyone experiencing this too ? Should we post a new bug ?

---

### Post by rizameister on 2010-06-30
> **_Narcisse_ said:**
> Hello,

Emesene started doing this a few days ago. I got exactly the same error message. I'll do a few searches and let you know if I find any workaround.

Anyone experiencing this too ? Should we post a new bug ?
This issue has been corrected in new version (1.6.2)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=578932](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=578932)

But there is no realase of 1.6.2 for ubuntu yet

---

### Post by devcando on 2010-06-30
> **rizameister said:**
> This issue has been corrected in new version (1.6.2)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=578932](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=578932)

But there is no realase of 1.6.2 for ubuntu yet

anyway you can use the ppa version or the source tarball for the moment...

---

### Post by SerafeimG on 2010-07-10
> **devcando said:**
> anyway you can use the ppa version or the source tarball for the moment...

What do you mean?
Explain me please...

---

### Post by kukker32 on 2010-07-10
i had a same looking problem with annoying error at start..

i ficed that by uninstall emesene COMPLETELY using synaptic..
and by disable any plugins to,,,
and did the same with all other Instant messaging programs to.

then i installed it again..

i don't know if it works for you... but maybe give it a try..

---

