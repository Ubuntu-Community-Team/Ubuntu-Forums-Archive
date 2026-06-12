---
title: "Updated Manager - Installation of update blocked."
date: 2012-04-21
forum: General Help
---

### Post by Ma5abre on 2012-04-21
Hi there

I am having trouble installing a software update from Medibuntu (which appears under 'Other Updates').  This was a PPA that I added myself from Launchpad.

It has always worked fine in the past but for some reason now that I have a new update available from that source, Update Manager wont let me install it and gives me the following message:

'Requires installation of untrusted packages'

'The action would require the installation of packages from unauthenticated sources.'

I have clicked on settings and checked under the 'Authentication' tab and I can see the software provider listed there. So I cannot understand why I am unable to install it.

Any help would be greatly appreciated.

---

### Post by plucky on 2012-04-21
> **Ma5abre said:**
> Hi there

I am having trouble installing a software update from Medibuntu (which appears under 'Other Updates').  This was a PPA that I added myself from Launchpad.

It has always worked fine in the past but for some reason now that I have a new update available from that source, Update Manager wont let me install it and gives me the following message:

'Requires installation of untrusted packages'

'The action would require the installation of packages from unauthenticated sources.'

I have clicked on settings and checked under the 'Authentication' tab and I can see the software provider listed there. So I cannot understand why I am unable to install it.

Any help would be greatly appreciated.

From [Here](http://medibuntu.org/repository.php)

Run this in a terminal ```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

This will install the Medibuntu repository and add the GPG key.

Good Luck

---

### Post by Ma5abre on 2012-04-23
Thank you 'plucky'. I shall give this a try and post the results.

---

### Post by Ma5abre on 2012-04-25
It worked!

Thank you so much for your help.

---

### Post by techsupport on 2012-04-25
> **Ma5abre said:**
> Hi there

I am having trouble installing a software update from Medibuntu (which appears under 'Other Updates').  This was a PPA that I added myself from Launchpad.

Any help would be greatly appreciated.

You can install it from the terminal instead like this, I just tested it yesturday and it works great, it is down the list here:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:guitar:

---

