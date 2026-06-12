---
title: "Can't uninstall a single package!"
date: 2006-03-21
forum: General Help
---

### Post by smilelover on 2006-03-21
Hi friends,
I recently wanted to try out Fluxbox. Synaptic tried to install it but when installing "menu" package - one of the deps - the process exited with error:

```

dpkg: error processing /var/cache/apt/archives/menu_2.1.25_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: unrecognized option `--menuentry=Debian menu'
        Try `install-info --help' for a complete list of options.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/menu_2.1.25_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Looks like it is all because of one line in postinst script :-k : ```
--menuentry=Debian menu
``` 

And since then, it's impossible to uninstall ANY SINGLE PACKAGE - all because of the "menu" pack. e.g.:
When uninstalling "menu" itself, apt-get dies of SIGABRT:

```

dpkg: error processing menu (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Neúsp&#283;&#353;n&#283; ukon&#269;en (SIGABRT)
android@hal10000:~/skripty$ Errors were encountered while processing:
 menu

```

Please help me, my system is unusable when I can't remove packages!! :???: 
Thanx...

---

### Post by skymt on 2006-03-21
[QUOTE=smilelover]
```

dpkg: error processing menu (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Neúsp&#283;&#353;n&#283; ukon&#269;en (SIGABRT)
android@hal10000:~/skripty$ Errors were encountered while processing:
 menu

```
[/QUOTE]

Did you try re-installing menu, like the message recommended?

---

### Post by smilelover on 2006-03-21
yes, every time I try ```
sudo apt-get install menu
``` it's the same. The problem is that the package in repos is simply corrupt. The line in postinit should not be there. In my point of view, at least.

---

