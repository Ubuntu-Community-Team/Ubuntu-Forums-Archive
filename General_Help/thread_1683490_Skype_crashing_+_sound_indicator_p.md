---
title: "Skype crashing + sound indicator p"
date: 2011-02-07
forum: General Help
---

### Post by damianburrin on 2011-02-07
There seems to be a documented issue with the latest version of skype crashing for no reason during chat sessions.

The following seems to completely resolve this issue

cd /usr/lib
sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3

Yet it screws up the sound indicator and sound control functions eg volume etc (though sound does work)

Ubuntu 10.04 (running NBR edition)

Any ideas?

Cheers
Damian

---

