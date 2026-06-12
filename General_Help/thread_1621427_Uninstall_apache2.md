---
title: "Uninstall apache2"
date: 2010-11-14
forum: General Help
---

### Post by thesuker on 2010-11-14
I used the command

dpkg -l | grep ^ii | grep apache2 | awk -F' ' '{ print $2 }'

to find apache2-related packages and

apt-get purge apache2 apache2-mpm-itk... etc to remove them.  I get the following error:

The following packages have unmet dependencies:
 apache2.2-common : Depends: apache2-utils but it is not going to be installed
E: Broken packages

How can I solve it? :S  already tried  sudo apt-get install -f  with no result

PD: what I basically want to do is delete apache2 and install it again with all config files back to default

---

