---
title: "Cannot connect to msn with Ubuntu 9.04 please help"
date: 2009-10-15
forum: General Help
---

### Post by sudoomar on 2009-10-15
Hello
Since i upgraded to ubunto 9.04 i am having problems connecting to msn.
My internet connection uses a proxy.I configured amsn but it did not work. neither Emesen nor Pidgin is working.
With amsn i get "error  connecting to server"
note that i have dualboot with vista and my windows live works
i heard that it is a bug in Ubuntu 9.04
please help

---

### Post by sudoomar on 2009-10-15
please help guys..

---

### Post by sudoomar on 2009-10-15
please help guys i've tried all msn clones for linuz but nothing is working

---

### Post by gwpritch on 2009-10-15
try removing your amsn then reinstalling it. I've been using it for months with Jaunty with no problems.

Use the purge option to get rid of all the old config files when removing.

```
sudo apt-get remove --purge amsn
```

---

### Post by mike555 on 2009-10-15
You are setting it to use your proxy server right?

---

