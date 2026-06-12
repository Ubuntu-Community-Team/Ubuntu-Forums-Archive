---
title: "Inconsistent Thunderbird Package"
date: 2009-08-24
forum: General Help
---

### Post by think13 on 2009-08-24
When installing updates today, I ran into a problem with the mozilla-thunderbird package.  I am not able to remove or reinstall with aptitude.
sudo aptitude remove mozilla-thunderbird
> dpkg: error processing mozilla-thunderbird (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
sudo aptitude reinstall mozilla-thunderbird
> E: I wasn't able to locate file for the mozilla-thunderbird package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the mozilla-thunderbird package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
I don't have a problem with removing Thunderbird-we don't use it on this computer.

Suggestions?

---

### Post by Sam Lars on 2009-08-25
Try downloading the packages from here
[http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/](http://us.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/)
and installing those.

---

