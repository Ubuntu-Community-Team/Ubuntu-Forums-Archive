---
title: "update init.d script"
date: 2011-05-27
forum: General Help
---

### Post by mulllhausen on 2011-05-27
i wrote a script and placed it in init.d some time ago to run on system startup. that all works well and good. but now i have changed the script (all i basically did was add the line echo 'afasdfasdfsf' > /tmp/x at the start), and the problem is that when i reboot, the old script still seems to be running (ie nothing shows up in /tmp/x). is this a standard feature of ubuntu and i simply need to reload the new script into some sort of cache?

cheers
mulll

---

### Post by mulllhausen on 2011-06-02
bump

---

### Post by Dave_L on 2011-06-02
The /tmp directory gets cleared on boot.  Maybe your script is writing to /tmp/x before that happens.

Try writing to a different directory, such as your home directory.

---

