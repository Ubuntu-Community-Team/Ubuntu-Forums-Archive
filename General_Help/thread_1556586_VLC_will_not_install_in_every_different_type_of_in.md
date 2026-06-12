---
title: "VLC will not install in every different type of installation method"
date: 2010-08-19
forum: General Help
---

### Post by sdmike6 on 2010-08-19
I'm running Lucid Lynx 64bit.

I tried installing VLC through the U-Software Center but it failed.

So I tried it through command line and that failed.

Here is the message I get:

```
apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlcReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
                      Depends: libvlc2 (>= 1.0.0~rc1) but it is not going to be installed
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
       Depends: libvlccore2 (>= 1.0.0~rc1) but it is not going to be installed
  vlc-plugin-pulse: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
                    Depends: libvlccore2 (>= 1.0.0~rc1) but it is not going to be installed
E: Broken packages
```

How can I fix this?

Regards,
~Mike

---

### Post by endotherm on 2010-08-19
well, it's the pair of plugins that it doesn't like. try just
```
sudo apt-get install vlc
```

---

### Post by luigi_mb on 2010-08-19
In Synaptic, search for "vlc" and then, even if the vlc entries are marked as not installed, try "Mark for complete removal", especially on "vlc-data". If that was the problem, Synaptic should now be able to install vlc.

/luigi

---

### Post by sdmike6 on 2010-08-20
I had already tried installing through Synaptic and I get a failed error.

I tried by command line just installing VLC and I get the same thing:

```
sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
       Depends: libvlccore2 (>= 1.0.0~rc1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.0.6-1ubuntu1.1) but it is not going to be installed
E: Broken packages
```

---

### Post by mc4man on 2010-08-20
Why don't you ck. your sources
System -> Admin. -> Software Sources
Make sure the 1st. 4 are checked in Ubuntu Software tab, while there also the 1st. 2 under the Updates tab.
Then click close and if prompted, - reload. If all were checked, (no reload prompt), then open a terminal and go 
```
sudo apt-get update 
```

Then try again

---

### Post by sdmike6 on 2010-09-23
> **mc4man said:**
> Why don't you ck. your sources
System -> Admin. -> Software Sources
Make sure the 1st. 4 are checked in Ubuntu Software tab, while there also the 1st. 2 under the Updates tab.
Then click close and if prompted, - reload. If all were checked, (no reload prompt), then open a terminal and go 
```
sudo apt-get update 
```

Then try again

I tried that and the same thing happens.

---

### Post by matborda on 2010-11-19
I tried **luigi_mb**'s method and it worked!!!

*Grazie mille!*

---

