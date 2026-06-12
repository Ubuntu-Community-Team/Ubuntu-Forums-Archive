---
title: "Permissions problem I think"
date: 2010-09-07
forum: General Help
---

### Post by dougalkerr on 2010-09-07
Hi folks I have a problem when trying to install Alien and get an error near the end of the install as follows;

Manifying blib/man1/alien.1p
Manifying blib/man3/Alien::Package::Deb.3pm
Manifying blib/man3/Alien::Package::Tgz.3pm
perl -i -pe "s/\@version\@/8.82/g" <alien.lsm.in >alien.lsm
perl -i -pe "s/\@version\@/8.82/g" <alien.spec.in >alien.spec
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/local/share/perl/5.10.0/Alien'
mkdir /usr/local/share/perl: Permission denied at /usr/share/perl/5.10/ExtUtils/Install.pm line 479

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at -e line 1
make: *** [pure_site_install] Error 13

Any ideas about overcoming this. I want to use Alien to convert .tgz to .deb as I have many times in the past but, after a fresh install of Jaunty onto an old machine I am having a bit of bother.
Thanks again for any suggestions.

---

