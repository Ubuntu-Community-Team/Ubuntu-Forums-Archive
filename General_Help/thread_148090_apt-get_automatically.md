---
title: "apt-get automatically"
date: 2006-03-21
forum: General Help
---

### Post by oly on 2006-03-21
is there away to install packages no questions asked ??

i have figured out apt-get install --force-yes -y but some packages ask for questions / passwords is there a way to skip this ??

i need to know for a script i have written which automaticall copys its own config file so the setup bit in apt-get is not needed.

---

### Post by gnu2tux on 2006-03-21
that's a bad idea - it's asking you these questions usually because you changed something, and something may break as a result of the changes apt is about to make.

---

### Post by oly on 2006-03-21
well except the question it asks are for an ldap admin password, which is then over written by my config script when setting up everything else, i just would have liked to make it so it does not ask questions which are not needed, i would not be suprised if it could not be done just thought i would ask.

---

