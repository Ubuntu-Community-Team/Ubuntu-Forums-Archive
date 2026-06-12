---
title: "Installed the Mozilla PPA, how to go back?"
date: 2010-01-15
forum: General Help
---

### Post by Vyrlokar on 2010-01-15
Trying to get [the thunderbird localization working ]("http://ubuntuforums.org/showthread.php?t=1381980")I briefly checked thunderbird 3, to see if it had the same issue. Now, the problem is, I accidentally installed new versions of Firefox 3.5 and XULrunner. If I remove them, then many other packets get removes due to dependencies. Same if I try to force version. If I simply remove the repos, then synaptic reports them as broken. Is there anything I can do to solve this? How stable are the updated versions? How often do they get updated?

---

### Post by slakkie on 2010-01-15
Could you do an apt-cache policy thunderbird please?

---

### Post by Vyrlokar on 2010-01-15
> **slakkie said:**
> Could you do an apt-cache policy thunderbird please?
I have no problems with the versions of thunderbird, the issue is with Firefox.

here are the results for them, using apt-cache policy

apt-cache policy firefox
firefox:
  Instalados: 3.5.8~hg20100113r26721+nobinonly-0ubuntu2~umd1~karmic
  Candidato: 3.5.8~hg20100113r26721+nobinonly-0ubuntu2~umd1~karmic
  Tabla de versión:
 *** 3.5.8~hg20100113r26721+nobinonly-0ubuntu2~umd1~karmic 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status
     3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Packages

Same versions for Firefox-3.5, firefox-branding,...

---

### Post by slakkie on 2010-01-15
I'm sorry (regarding thunderbird), but thnx for the apt-cache info for the correct package :).
 
You can downgrade firefox (without too much trouble). The only issue is, as long as you keep that PPA in your sources.list every upgrade you do will also upgrade firefox from that PPA. Which can be anoying.. 

You might want to have a read here: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)
It is from my blog, but it deals with mixing your various repo's and controlling what you install from them. 

In short

```

sudo vi /etc/apt/preferences

```
```

Package: *
Pin: origin ppa.launchpad.net
Pin-Priority: 100

Package: thunderbird
Pin: origin ppa.launchpad.net
Pin-Priority: 990 

```

This should enable you to install thunderbird from the ppa while denying other packages to be installed from PPA's. 

Hope this helps.

---

