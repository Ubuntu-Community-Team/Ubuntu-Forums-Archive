---
title: "flashplugin64 no installation candidate"
date: 2011-10-10
forum: General Help
---

### Post by CaptainMark on 2011-10-10
```
mark@desktop:~$ sudo apt-get install flashplugin64-installer 
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin64-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'flashplugin64-installer' has no installation candidate

```After a recent reinstall of natty Ive got this error from when installing the package flashplugin64-installer I usually install this and I've not seen this one before, what does it mean?

---

### Post by gandaran on 2011-10-10
there isn't any flashplugin64-installer package on the Ubuntu system repository's, you have to add the PPA flash repository to get this package.

---

### Post by haqking on 2011-10-10
> **gandaran said:**
> there isn't any flashplugin64-installer package on the Ubuntu system repository's, you have to add the PPA flash repository to get this package.

I think the PPA has been deprecated:

ppa:sevenmachines/flash

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

[http://www.ubuntuupdates.org/packages/show/301005](http://www.ubuntuupdates.org/packages/show/301005)

mind you i might be talking rubbish as i dont use 11.04 but i know i used this ppa in a VM

[Flash-Aid ]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")is what i used after that though

---

### Post by CaptainMark on 2011-10-10
i have the ppa installed already as i say i use this package all the time but never had this problem, flash aid does a totally different thing, flashaid removes conflicting flash plugins, where as flasplugin64 is a native 64bit plugin instead of the old 32bit one in a wrapper

thanks for pointing this out haqking, adobe has rolled official native 64 bit into the flashplugin-installer package, cool,

---

