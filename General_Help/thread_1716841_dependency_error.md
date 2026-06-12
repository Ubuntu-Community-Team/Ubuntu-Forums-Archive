---
title: "dependency error"
date: 2011-03-29
forum: General Help
---

### Post by John Krow on 2011-03-29
Hello all, I made a bit of a schoolboy error with Ubuntu. I was without an internet connection so attempted to install OpenShot manually, using .debs. Naturally there were too many dependencies to chase up but I did install some of them...!

Now my connection is back i tried to install openshot (from the recommended ppa) as well as upgrading vlc (from the recommended ppa). Naturally OpenShot won't install as I have my dependencies all over the place. I was wondering if there was a way to track and uninstall/purge the last few manually installed packages, and if then installing openshot would proceed normally.

Here was the relevant  output:
```
crow@nest-desktop:~$ sudo apt-get install openshot openshot-doc vlc vlc-plugin-pulse mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libavformat52: Breaks: mplayer (< 2:1.0~rc4~) but 2:1.0~rc3+svn20090426-1ubuntu16.1+medibuntu1 is to be installed
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.1.8-1ubuntu1~ppa1~lucid1) but it is not going to be installed
  openshot: Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not going to be installed or
                     python-mlt but it is not installable
  vlc: Depends: vlc-nox (= 1.1.8-1ubuntu1~ppa1~lucid1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1.1.8-1ubuntu1~ppa1~lucid1) but it is not going to be installed
  vlc-plugin-pulse: Depends: vlc-nox (= 1.1.8-1ubuntu1~ppa1~lucid1) but it is not going to be installed
E: Broken packages

```

---

### Post by zvacet on 2011-03-29
```
sudo apt-get -f install
```

---

### Post by John Krow on 2011-03-29
Thanks very much. It didn't work but it was a good pointer. What I did was run aptitude, which suggested removing certain packages to resolve the dependencies. My command ran ok, and I was then able to re-install the packages aptitude removed in any of the usual ways. Thanks again, this is now solved.

---

