---
title: "Compile error from gcolor.sourceforge.net"
date: 2006-03-07
forum: General Help
---

### Post by calutateo on 2006-03-07
Dear all,

While compiling gcolor from [http://gcolor.sourceforge.net](http://gcolor.sourceforge.net) I get the following error:

[INDENT][...]
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE_CFLAGS...
checking for PACKAGE_LIBS...
configure: error: Package requirements (gtk+-2.0 >= 2.4) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PACKAGE_CFLAGS and PACKAGE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
[/INDENT]

Any ideas?

Regards, Carsten

---

### Post by taurus on 2006-03-07
Sounds like you need gtk+ and gtk+_dev.  Open up synaptic and search for gtk+ packages then...

---

### Post by Enissay on 2007-11-27
I got the same problem under Gutsy....How to fix the problem please??

---

### Post by FuturePilot on 2007-11-27
Gcolor2 is in the repos. You might want to try
```
sudo apt-get install gcolor2
```

---

