---
title: "Software installation problem in Ubuntu 11.04"
date: 2011-04-29
forum: General Help
---

### Post by pezzonovante on 2011-04-29
I have installed Ubuntu 11.04 yesterday. I did a clean install. Now, I have downloaded the Google Chrome dev channel packages from the Google web site. Now if I run this command:
*sudo dpkg -i google-chrome-unstable_current_amd64.deb*

Google Chrome doesn't install. I get the following error:

[I](Reading database ... 130013 files and directories currently installed.)
Preparing to replace google-chrome-unstable 12.0.742.12-r83281 (using google-chrome-unstable_current_amd64.deb) ...
Unpacking replacement google-chrome-unstable ...
dpkg: dependency problems prevent configuration of google-chrome-unstable:
 google-chrome-unstable depends on libnss3-1d (>= 3.12.3); however:
  Package libnss3-1d is not installed.
dpkg: error processing google-chrome-unstable (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 google-chrome-unstable[/I]

Can anyone suggest a solution?

---

### Post by pezzonovante on 2011-04-29
I have just managed to solve the problem. I changed the update servers. Looks like the default server wasn't working properly.

---

### Post by sudo_!! on 2011-09-10
Could you please specify what you changed?

I am encountering the same problem here...

---

### Post by raja.genupula on 2011-09-10
at update manager-->settings-->ubuntu software 

download from , in that options you can change your download sever

---

