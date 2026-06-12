---
title: "ssh non X11 forwarding"
date: 2012-02-11
forum: General Help
---

### Post by gr3g0r on 2012-02-11
Hi Guys,

i am looking for a way to connect to a remote machine and using the remote X11 session. I don't want to forward anything to my local machine, i just would like to forward the output to /dev/null if possible.

best regards.

Gregor

---

### Post by gr3g0r on 2012-02-11
ok a simple 
```
export DISPLAY=:0
```does the trick

---

### Post by markbl on 2012-02-11
ssh -x

---

