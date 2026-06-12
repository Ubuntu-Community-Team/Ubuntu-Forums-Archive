---
title: "I cannot upgrade VLC or install Pidgin and other programs in Ubuntu 10.04"
date: 2011-07-19
forum: General Help
---

### Post by Rytron on 2011-07-19
Hi.

Recently I selected 'Mark All Upgrades' in Synaptic. This forced me to remove imagination, picard and pidgin [image attached].

Also I cannot upgrade VLC as I get this message in Synaptic:
vlc:
```
 Depends: vlc-nox but it is not going to be installed
 Depends: libavcodec52 but it is not going to be installed or
 	libavcodec-extra-52 (>=4:0.6-1~) but 4:0.5.1-1ubuntu1.1 is to be installed
 Depends: libavutil50 (>=4:0.6-1~) but it is not installable or
 	libavutil-extra-50 (>=4:0.6-1~) but it is not installable
  Depends: libqtcore4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.2 is to be installed
  Depends: libstdc++6 (>=4.5) but 4.4.3-4ubuntu5 is to be installed
 Depends: libva-x11-1  but it is not installable
 Depends: libva1  but it is not installable
 Recommends: vlc-plugin-notify but it is not going to be installed
 Recommends: vlc-plugin-pulse but it is not going to be installed
```

Here are the errors I get when I try to install imagination, picard and pidgin.

```
imagination:
 Depends: libgdk-pixbuf2.0-0 (>=2.22.0) but it is not installable
 Depends: libsox1b (>=14.3.1) but it is not installable
 Recommends: libavutil-extra-50  but it is not installable
```

```
picard:
 Depends: libavcodec52 but it is not going to be installed or
 	libavcodec-extra-52 (>=4:0.6-1~) but 4:0.5.1-1ubuntu1.1 is to be installed
 Depends: libavformat52 but it is not going to be installed or
 	libavformat-extra-52 (>=4:0.6-1~) but 4:0.5.1-1ubuntu1.1 is to be installed
```

```
pidgin:
 Depends: libgdk-pixbuf2.0-0 (>=2.22.0) but it is not installable
  Depends: libpurple0 (>=1:2.8.0) but 1:2.6.6-1ubuntu4.3 is to be installed
  Depends: gconf2 (>=2.28.1-2) but 2.28.1-0ubuntu1 is to be installed
  Depends: perl-base (>=5.10.1-17ubuntu4.1) but 5.10.1-8ubuntu2.1 is to be installed
 Recommends: pidgin-libnotify but it is not going to be installed
```

---

### Post by GeoffreyBernardo on 2011-07-19
What you should do is to install all the dependent packages, e.g. for vlc, you get the message "Depends: vlc-nox". That tells you to install vlc-nox first. The reason that it says that vlc-nox will not be installed is because vlc-nox is not marked for installation.

In Synaptic package manager, in the searc box, type in vlc-nox. Then click on the checkbox next to vlc-nox, and click on Mark for Installation on the list that appears. Then click Apply on the toolbar.

Do that for each of the dependent packages.

---

### Post by Rytron on 2011-07-19
> **GeoffreyBernardo said:**
> What you should do is to install all the dependent packages, e.g. for vlc, you get the message "Depends: vlc-nox". That tells you to install vlc-nox first. The reason that it says that vlc-nox will not be installed is because vlc-nox is not marked for installation.

In Synaptic package manager, in the searc box, type in vlc-nox. Then click on the checkbox next to vlc-nox, and click on Mark for Installation on the list that appears. Then click Apply on the toolbar.

Do that for each of the dependent packages.

This is odd. [COLOR="Indigo"]vlc-nox[/COLOR] is already installed. :confused:

---

### Post by Rytron on 2011-07-19
Also other dependencies are also either installed or unavailable in synaptic. So this is what is called dependency hell.

If I install [COLOR="Indigo"]libavcodec52[/COLOR], it forces me to remove many other programs.

Edit: Would restoring the file [COLOR="DarkGreen"]/etc/apt/sources.list[/COLOR] remedy this dependency mess?

---

### Post by Rytron on 2011-07-19
I went into synaptic and then repositories. I played around with unchecking items in Ubuntu Software tab, then Other Software tab. I reloaded and was able to install Picard, Pidgin & Imagination with no problem.
I found the culprit [image attached]. So I renamed [COLOR="DarkRed"]natty-getdeb[/COLOR] part to [COLOR="DarkOrange"]lucid-getdeb[/COLOR] [image attached]. Done and dusted.

---

