---
title: "Can I remove XTerm?"
date: 2012-08-04
forum: General Help
---

### Post by jonesyp on 2012-08-04
Hi,

I am trying to get space on my system and remove applications I do not use.  When I try and remove xterm I get the following message:
[B]
If you uninstall XTerm. future updates will not includes new items in the Ubuntu desktop system set. Are you sure you want to continue?[/B]

Could anybody help me in understanding this?

Best wishes

Peter Jones

---

### Post by codemaniac on 2012-08-04
> **jonesyp said:**
> Hi,

I am trying to get space on my system and remove applications I do not use.  When I try and remove xterm I get the following message:
[B]
If you uninstall XTerm. future updates will not includes new items in the Ubuntu desktop system set. Are you sure you want to continue?[/B]

Could anybody help me in understanding this?

Best wishes

Peter Jones

You need to use Synaptic Package Manager or Software Center to  check you are not removing anything desirable along with the program you do not need. They will prompt if anything other than the program in question is to be removed.

---

### Post by jonesyp on 2012-08-04
I have included the message I get when I try and uninstall with software center in my original post.

Regards

Peter Jones

---

### Post by codemaniac on 2012-08-04
removing 'xterm' package will also remove the 'ubuntu-desktop' package it flags . 'ubuntu-desktop' is a required package if you ever intend to upgrade to a new version of ubuntu, so removing this is not desirable.

---

### Post by ajgreeny on 2012-08-04
However, even if you do remove it the saving of space will be just over 1MB, surely hardly worth the trouble.

If you always do a clean install rather than an update from one distro version to the next, removal of ubuntu-desktop package is not important.  It does not actually contain any packages but is simply a list of dependent packages needed for the full ubuntu OS.

---

### Post by dcstar on 2012-08-06
> **ajgreeny said:**
> However, even if you do remove it the saving of space will be just over 1MB, surely hardly worth the trouble.

If you always do a clean install rather than an update from one distro version to the next, removal of ubuntu-desktop package is not important.  It does not actually contain any packages but is simply a list of dependent packages needed for the full ubuntu OS.

[LIST=1]
[*]These people who try and "clean up" their Ubuntu systems are not just wasting their own time for little (if any gain), they usually break things and then fill these forums with their self-caused issues.
[*]Breaking any Ubuntu meta-package can have consequences for upgrades during the support lifetime of the release, it is not really good practice to do it.
[/LIST]

---

### Post by ajgreeny on 2012-08-06
Yes, I agree with what you say in general terms, and I accept that the package description says it is best not removed, but as far as I'm aware, ubuntu-desktop package is only used when first installing, to make sure that all other required packages are included in the ubuntu install, and again is needed when doing a distro update from one version of ubuntu to the next.

Never having done a distro upgrade I could be wrong about that but I don't think I have ever seen or heard of problems running and updating ubuntu in a normal manner, (not distro updating) after removal of the ubuntu-desktop package.

I realise we are getting away slightly from the original query, but perhaps this is worth more discussion.

---

