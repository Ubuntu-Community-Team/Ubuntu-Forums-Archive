---
title: "Pidgin does not start: version conflict with libpurple"
date: 2010-02-05
forum: General Help
---

### Post by Daniel_le_Rouge on 2010-02-05
Hello!

I have a problem with Pidgin. In does not start anymore.

The error message is this one here:

```
pidgin: symbol lookup error: pidgin: undefined symbol: purple_theme_loader_get_type
```

I also know the reason which is old version of libpurple.

```

daniel@daniel-laptop:~$ pidgin -v
Pidgin 2.6.5 (libpurple 2.5.5)
```

The problem is that I do not know how to fix it. I have compiled Pidgin myself and afterwards there was a reinstallation through Synaptics.

What can I do to fix the problem? I am using Ubuntu 9.10.

Thanks!

Daniel

---

### Post by howefield on 2010-02-06
Remove what you installed and then reinstall using the instructions from the pidgin website. This will give your the latest version and keep it up to date.

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

---

