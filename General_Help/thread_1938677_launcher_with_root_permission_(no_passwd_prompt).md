---
title: "launcher with root permission (no passwd prompt)"
date: 2012-03-10
forum: General Help
---

### Post by ohnonot on 2012-03-10
hello!

i would like to have a launcher on my desktop to change my cpu scaling governor to "userspace" and then set it to the highest frequency.

at the moment i accomplish this with these commands:```
sudo cpufreq-set -c 0 -g userspace
sudo cpufreq-set -c 0  -d 2GHz
sudo cpufreq-set -c 0  -f 2GHz
```but i would like to automate this, not having to type passwords.
so right now i have a launcher on my desktop pointing to a shellscript, and i have added those 2 lines to sudoers:```
%myusername LOCAL=NOPASSWD:/home/myusername/.config/boostcpu.sh
%myusername LOCAL=NOPASSWD:/usr/bin/cpufreq-set
```- but it doesn't work.

there's a few posts dealing with similar things but i'm really confused now and so ask for help?

---

