---
title: "Problem updating apt-get"
date: 2010-06-13
forum: General Help
---

### Post by chairmanrob on 2010-06-13
I can't seem to update apt-get. Whenever I try to I get this error.


[LIST]
[*]robert@ubuntu:~$ sudo apt-get update
E: The method driver /usr/lib/apt/methods/httP could not be found.
E: The method driver /usr/lib/apt/methods/httP could not be found.
[/LIST]

---

### Post by MooPi on 2010-06-13
Can you post the contents of your /etc/apt/sources.list

---

### Post by chairmanrob on 2010-06-13
> **MooPi said:**
> Can you post the contents of your /etc/apt/sources.list
I got it to update. Thank you, you pointed me in the right direction. The problem was that the "p" in http was capitalized.

---

