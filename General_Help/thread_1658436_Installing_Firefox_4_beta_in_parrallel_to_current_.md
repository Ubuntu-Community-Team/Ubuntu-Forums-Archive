---
title: "Installing Firefox 4 beta in parrallel to current version ???"
date: 2011-01-02
forum: General Help
---

### Post by astrobob.tk on 2011-01-02
Hello Ubuntuers,

can someone guide me in the installation of firefox 4 beta on Ubuntu 10.04 LTS in parallel with my current ff 3.6.13 ??? if its anyway possible ?

thanks

---

### Post by lidex on 2011-01-02
Sure it can be done. See this page, click on installation method #1: [http://www.webgapps.org/firefox/installing-other-versions](http://www.webgapps.org/firefox/installing-other-versions)

---

### Post by gufide on 2011-01-02
yes, using the firefox ppa. Just add it:
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update && apt-get install firefox-4.0
```

---

### Post by lidex on 2011-01-02
> There are some things you should be aware before using a PPA to upgrade Firefox:

    some ppa repositories like ubuntu-mozilla-daily update not only Firefox, but also other Mozilla applications, like Thunderbird.
    some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
    some repositories like ubuntu-mozilla-daily upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.

Taken from the link I posted above.

---

