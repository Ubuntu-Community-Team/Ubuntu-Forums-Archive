---
title: "Cant Remove Package"
date: 2009-12-04
forum: General Help
---

### Post by Chamillionaire2 on 2009-12-04
What's Up?

OK, So I've been fiddling with making .deb's and now i cant install any more .deb's or open synaptic manager, I tried forfully purging the package "theme" but with no luck.

```
zack@zack-desktop:~$ sudo dpkg --remove --force-remove-reinstreq theme
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 207820 files and directories currently installed.)
Removing theme ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing theme (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 theme
zack@zack-desktop:~$
```

Anyone know whats wrong?

Thanks Bye.

---

### Post by spiderbatdad on 2009-12-04
don't know but have you tried running dpkg --configure -a and then using the purge option?

---

### Post by Chamillionaire2 on 2009-12-05
> **spiderbatdad said:**
> don't know but have you tried running dpkg --configure -a and then using the purge option?

Nope that dident work, I tried using the janitor app, But i got "E:Sub-process /usr/bin/dpkg returned an error code (1)"

Any ideas?

**Added, Found this
```
1) use the following command to open nautilus with root privileges:
sudo nautilus

2) open the file:
/var/lib/dpkg/status

3) search for "virtualbox" you should find the following lines:
Package: virtualbox
Status: install reinstreq half-installed
Priority: optional
Section: misc
Version: 1.3.6_Ubuntu_edgy

4) Remove these lines from the file and save

You should now be able to use synaptic again!
```
Thanks Bigyoy

---

