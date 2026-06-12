---
title: "Ubuntu 11.04 Software Center won't Open"
date: 2011-06-12
forum: General Help
---

### Post by FALL3N1 on 2011-06-12
When I click the Software Center icon, it does not open.. and I already tried 'sudo apt-get update'... that's the answer I found like 20x when I did searches... so what else should I do to fix this?

---

### Post by mörgæs on 2011-06-12
Hi, welcome to the fora.

It was a good answer you found! Please boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

and post the error messages, if any.

---

### Post by FALL3N on 2011-06-13
Tried that, before, didn't work, it was something with my python files... the dependencies were broken or something..   Good news though, I reinstalled Ubuntu and now everything works fine!  Thanks for the answer though.  I figured that since I hadn't put most of my data back onto the computer yet, it wouldn't be a big deal to reinstall the system, as it takes like 25 minutes..  Thanks again!

---

### Post by mörgæs on 2011-06-13
You are welcome. Please mark the thread 'solved'.

If only people were a little less afraid to reinstall their systems, then half of the problems reported here would be solved already.

---

### Post by FALL3N on 2011-06-15
ok, thanks again!

---

### Post by FALL3N on 2011-06-15
$delete

---

