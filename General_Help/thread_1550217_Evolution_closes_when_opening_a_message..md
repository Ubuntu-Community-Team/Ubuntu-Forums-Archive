---
title: "Evolution closes when opening a message."
date: 2010-08-10
forum: General Help
---

### Post by techmonkey1 on 2010-08-10
Evolution 2.28.3
Ubuntu 10.04 Lucid Lynx

When I click a message to open, Evolution closes immediately.
The log shows this error:
kernel: [ 6122.611585] evolution[6000]: segfault at 0 ip 06217ea5 sp b2655fe0 error 4 in libcamelimap.so[61f9000+23000]

How do I fix this? I tried uninstalling and then reinstalling Evolution. Did not work.

---

### Post by techmonkey1 on 2010-08-10
I solved my problem with 2.28.3 by installing 2.30.

I used the following commands to install 2.30:
sudo add-apt-repository ppa:jacob/evo230 && sudo apt-get update
sudo apt-get install evolution

---

