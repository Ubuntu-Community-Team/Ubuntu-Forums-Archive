---
title: "wont let me install updates."
date: 2011-08-04
forum: General Help
---

### Post by p.wolf on 2011-08-04
hey i cant install important security updates! and now my sound has gone and ******, making some kinda...well i would compare it to...hmm, maybe a tinny sound? or somethin. kinda weird i know >.>
any help?

---

### Post by Beacon11 on 2011-08-04
Hmm. A little more information would be nice, for instance, what makes you say you can't install security updates? Do you get an error message? Does this mean you can install all updates EXCEPT security ones?

---

### Post by p.wolf on 2011-08-07
i get an error message and it wont install any, it just mentions the security ones though.
the sound is very annoying, i have to restart my computer to fix it then it keeps happening :/

---

### Post by wildmanne39 on 2011-08-07
Hi run this command and post the error message here please:
```
sudo apt-get update && sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by p.wolf on 2011-08-08
```
W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

when i ran the commands it returned this

---

### Post by garvinrick4 on 2011-08-08
Here is your medibuntu key:
```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
``````
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by garvinrick4 on 2011-08-08
For the 404 fail:
Go to software sources and open other software tab and uncheck that ppa.xbmc it is
not good now 404 means it cannot find it there. (xbmc does not have a natty ppa)
Here is list of ppa's xbmc is there just click on your version.
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

> ##hey i cant install important security updates!Nothing to do with security updates, seems as though you have been installing ppa's
I would have to think.

---

