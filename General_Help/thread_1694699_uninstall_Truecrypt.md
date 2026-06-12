---
title: "uninstall Truecrypt"
date: 2011-02-24
forum: General Help
---

### Post by kingwill on 2011-02-24
Hi

I installed Truecrypt by downloading the package from their website and then using the Software Centre to install it.

It's not what I want but now I can't find a way to un-install it. I've tried going by the Software Centre and Synaptic but it is not displayed. 

I've also tried the sudo apt-get remove truecrypt approach in the terminal but it tells me I can't remove a virtual package from there.

I didn't install it as a virtual package so I'm a bit non-plused over that.

Is there another way to uninstall unwanted programs?

---

### Post by choochus on 2011-03-17
I see its been a couple weeks, so you may have found the solution. For anybody stumbling across this thread:
there should be a script in /usr/bin named "truecrypt-uninstall. sh". You can invoke it using the following command
```
sudo /usr/bin/truecrypt-uninstall. sh
```

Cheers!

---

