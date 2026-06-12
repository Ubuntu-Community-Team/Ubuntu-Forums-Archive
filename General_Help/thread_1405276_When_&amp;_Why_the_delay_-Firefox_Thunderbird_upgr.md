---
title: "When &amp; Why the delay -Firefox Thunderbird upgrade version"
date: 2010-02-12
forum: General Help
---

### Post by ddwwdd on 2010-02-12
Having unsuccessfully checked through the forum for this, I wonder why ubuntu software store & upgrade manager & Synaptic Package Manager all show the most recent version of Mozilla Thunderbird as 2.0.0.23 whereas the Mozilla web site indicates the latest linux version to be 3.0.1?

Similarly for Firefox 3.5.7 compared to version 3.6 available from Mozilla?

Is it because Ubuntu does significant testing before migrating (with or without modifications) the Mozilla products?  If so, why does it take so long?  After all, these are important programs an include security issues as well.

Even apt-get brings the older versions.  Please advise?  TIA!

---

### Post by OrangeCrate on 2010-02-12
Once a version of Firefox and Thunderbird are set into a Ubuntu release, they will be there for the life of that version (with very rare exceptions). They will, of course, be updated on a regular basis for security issues, but you won't see a new version until the next Ubuntu release. (For example - I'm typing this on Firefox 3.6, but only because I'm using Ubuntu 10.04 Lucid.)

You can go get them and install the newer versions on your own, but if you want "official" installs, and updates through the repositories, you will need to wait for the next Ubuntu release.

---

### Post by hemimaniac on 2010-02-12
1 must realize, that "packages' for your particular distro need to follow a few (sometimes length) steps before even considered for release.

1- testing and stability

2- acceptance by developers to test, package then release

3- addition to a repo or PPA

now one also needs to remember that it is all done via volunteers and community members, just because mozilla released it doesn't necessarily mean its right for the distro at the time of release. In windows for the most part there are only a couple of packages, for *unix there can be oodles of packages for each flavor (flux, gnome, kde etc etc) as all need to be packaged differently and mozilla is NOT gonna do that on their end.

One look through the forums under the Firefox search criteria will point out the answer to your question REAL quick, imo too many people run for the latest and greatest BEFORE ever reading the install instructions, release notes and, know issues or even understanding the whole stability concept that EVERY flavor of *unix strives for. My opinion if it isnt included in the original release or recently added to your specific distro's repo, don't do it, it will save 10-15 % of the "Installed latest build of "whatever here" and now "this/that" doesn't work now" threads.

If you would like the latest and greatest, read up on "bleeding edge" or there is always windblows.

---

### Post by lovinglinux on 2010-02-12
See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

