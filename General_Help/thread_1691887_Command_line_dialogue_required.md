---
title: "Command line dialogue required"
date: 2011-02-20
forum: General Help
---

### Post by lonewolf88 on 2011-02-20
Hi,

Scenario as follows.

Tried to upgrade my Toshiba T110 laptop from netbook remix 10.04 to 10.10 through the Ubuntu upgrade window (new version available button).

Now boots only in text screen.  All worked fine in 10.04

Done various things from research and suggestions, but still in text only mode boot up screen.  Command to start X fails.

In another forum here a user suggested that I may have lost my graphics drivers.

Can I reinstall these from a command line in the text boot up screen?

The graphics card is "Mobile IntelGM45 Express Chipset".

Can anyone help?

Thanks!

---

### Post by cariboo on 2011-02-20
It sounds more like your upgrade didn't complete. Have you tried the following commands:

```
sudo apt-get update
```

then

```
sudo apt-get -f install
```

then

```
sudo apt-get dist-upgrade
```

---

### Post by lonewolf88 on 2011-02-20
> **cariboo907 said:**
> It sounds more like your upgrade didn't complete. Have you tried the following commands:

```
sudo apt-get update
```then

```
sudo apt-get -f install
```then

```
sudo apt-get dist-upgrade
```

Thanks.  No difference! :(

---

### Post by bronquel on 2011-02-20
I've had that happen to me before.  For me i back up my files and install the version of ubuntu you want.  not sure how much you have customized ubuntu - which would increase the amount of time to reinstall and configure the system to your liking.

the main reason i reinstall is that you have a guaranteed fix in a predictable amount of time, usually a half hour to install ubuntu and an hour to configure/setup stuff - mostly time waiting for things to download or install.

---

