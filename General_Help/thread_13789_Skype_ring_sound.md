---
title: "Skype ring sound"
date: 2005-02-02
forum: General Help
---

### Post by pavkonti on 2005-02-02
when someone calls me I do not have ring sound (it is not ringing). I can talk with the other person.

---

### Post by zeldan on 2005-06-25
I had the same problem and resolved it in this way:

cd /opt/skype
./skype


the wrong way was executing skype from another directory
/opt/skype/skype

because skype serches for sounds in current directory

---

### Post by nmsa on 2006-10-09
Hello,
 true, works, but I always have to lunch it from a terminal
 this is what I did:
 cd /usr/bin
 mv skype skype-old
 edit skype adding these lines in:
```
#!/bin/bash
cd /opt/skype-1.2.0.18
./skype
```
sudo chmod +x skype
and works

ok? better way to do it?
Greetings

---

