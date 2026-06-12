---
title: "Error configuring indicator-sensors installation on 11.04"
date: 2011-08-01
forum: General Help
---

### Post by thetouristbr on 2011-08-01
Hello everyone,

I am trying to install the indicator-sensors-0.1 beta for Unity on Ubuntu 11.04 amd64 (2.6.38-10-generic).

This package is available at [https://launchpad.net/indicator-sensors](https://launchpad.net/indicator-sensors)

However, i get the following error when running the command ./configure :


```

checking for APPINDICATOR... no
configure: error: Package requirements (appindicator-0.1 >= 0.0.7) were not met:

No package 'appindicator-0.1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables APPINDICATOR_CFLAGS
and APPINDICATOR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I checked Synaptic list and verified that the following packages are already installed:

[LIST]
[*] girl1.2-appindicator-0.1
[*] python-appindicator
[*] libappindicator0.1-cil
[*] girl1.2-appindicator3-0.1
[/LIST]

I cannot find any other package with "appindicator" in its name.

How can I fix this problem?

---

