---
title: "Help needed to restore after Python removal"
date: 2010-06-24
forum: General Help
---

### Post by RebeccaB37 on 2010-06-24
Hi there everyone,

Serious help needed with this one as I have FUBR, I think. :(

Yesterday I upgraded from 8.04 to 10.04 without issue. Today I was trying to set up the development version of GRASS7, which required changes to Python 2.6. Stupidly instead of reinstalling, I managed to select remove for all python except minimal for all versions.

Ubuntu of course now boots in low graphics mode. Is there a way I can restore it to the default without reinstalling from scratch?

I would really appreciate any help you could offer on this!

Rebecca

---

### Post by oldfred on 2010-06-24
I am suprised you can even get to a low graphics mode. Did you install any hardware drivers for your video card?

I would go thru the full houseclean and update process, perhaps reinstalling the desktop will update some things also.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by RebeccaB37 on 2010-06-25
Thanks for the advice oldfred, because this is my primary machine I had to get ubuntu back up an running I reinstalled on a new partition yesterday before you had chance to reply.

This worked to a point but I have started a new thread asking for advice about removing the partition with the broken version to reallocate
[http://ubuntuforums.org/showthread.php?p=9508480#post9508480](http://ubuntuforums.org/showthread.php?p=9508480#post9508480)

Thanks again for taking the time to answer!

---

### Post by asearle on 2012-03-27
Dear OldFred,

Many, many thanks:  This script really sorted me out.

I ran just the "ubuntu-desktop" section and now my whole system is back up and running.

Bravo, bravo, bravo!

Regards,
Alan Searle

---

