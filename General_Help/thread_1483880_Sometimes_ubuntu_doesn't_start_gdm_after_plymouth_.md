---
title: "Sometimes ubuntu doesn't start gdm after plymouth and hangs"
date: 2010-05-15
forum: General Help
---

### Post by connexion2000 on 2010-05-15
Hi,
I have a problem. Sometimes ubuntu doesn't fully boot. Plymouth disappears and gdm should appear, but it hangs. With last message on console (GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)). I understand that this warning has nothing in common with a problem. When hanged I can press ctrl+alt+delete and computer reboots, then boots fine to gdm. This is very annoying. What might be wrong?

---

### Post by connexion2000 on 2010-05-17
*bump*

---

### Post by mpnordland on 2010-12-01
here is what to do:
first hit ctrl+alt+f1
then type your username and password.
then type 
```
sudo apt-get purge gdm
```
then type your administrative password.
make sure to approve of the changes
then type ```
sudo apt-get install gdm
```
after that
```
sudo start gdm
```
then you will be back in business

---

