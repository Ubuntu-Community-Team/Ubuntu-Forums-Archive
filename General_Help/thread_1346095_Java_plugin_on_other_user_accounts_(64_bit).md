---
title: "Java plugin on other user accounts (64 bit)"
date: 2009-12-04
forum: General Help
---

### Post by tbzep on 2009-12-04
I installed the latest 64 bit Sun Java with great success by following the guide located here: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

However, when I tried to link the plugin from the other user accounts, I was unable to do so. These are the instructions I was unable to follow.  

> Other user accounts: repeat two commands

Are there any other user accounts on the computer? Then repeat the following two commands in each user account:

rm ~/.mozilla/plugins/libnpjp2.so

and then:

ln -s /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

---

### Post by quixote on 2009-12-05
If this is the first install of java, there may not be a libnpjp2.so in users' home dirs.  Then the rm command would seem to not work (because there's nothing to remove).  libnpjp2.so doesn't necessarily wind up in that directory.  On my system, for instance, it's in /usr/lib/firefox-addons/plugins/.  You could try find to see where it is (start from /usr, not your home directory):```
find . -type f -name 'libnpjp2.so'
``` It'll take a while, because /usr is huge. If it doesn't show up, try /opt.  (Or, if you installed as a user rather than sudo, then do try your /home directory.)  Once you've found it, make a link like they say, only with the right directory as a source.

---

