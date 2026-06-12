---
title: "Applications shutting down"
date: 2011-05-27
forum: General Help
---

### Post by aleifr on 2011-05-27
It's really weird, some applications simply don't start up. Skype for one, just shuts down before logging in, and Calibre shuts down instantly, when I try to run it. I've tried to remove and re-install it, but that doesn't do any good.

What the hell does one do about that? =/

---

### Post by LordNeo on 2011-05-27
Try to run them from console, it could throw some information.
Also try to run them from console using sudo, to check if it's something with your user profile.

Best regards

---

### Post by aleifr on 2011-05-27
> **LordNeo said:**
> Try to run them from console, it could throw some information.
Also try to run them from console using sudo, to check if it's something with your user profile.

Best regards

```
aleifr@olavur-laptop:~$ sudo calibre
[sudo] password for aleifr: 
Traceback (most recent call last):
  File "/usr/bin/calibre", line 18, in <module>
    from calibre.gui2.main import main
  File "/usr/lib/calibre/calibre/__init__.py", line 14, in <module>
    from calibre.startup import plugins, winutil, winutilerror
  File "/usr/lib/calibre/calibre/startup.py", line 51, in <module>
    set_translators()
  File "/usr/lib/calibre/calibre/utils/localization.py", line 66, in set_translators
    lang = get_lang()
  File "/usr/lib/calibre/calibre/utils/localization.py", line 33, in get_lang
    'LC_MESSAGES', 'LANG'])[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_DK
```

I don't know what the hell that is. =/ Thanks for your reply.

Calibre is a ebook reader and manager, if anyone has any doubts about that...

[EDIT] It looks like Calibre has a problem with my locale setting in a python file.

---

