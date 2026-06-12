---
title: "Run command at power source change/ resume"
date: 2010-12-12
forum: General Help
---

### Post by hagga03 on 2010-12-12
Ubuntu enables power management on my network card when it switches to battery power, which significantly slows down the connection speed. To disable this I run the following command in the terminal:

sudo iwconfig eth1 power off

This solves the problem, however it needs to be typed every time I switch to battery power, resume from sleep or boot up the system.

How can I have the system run this command automatically in all of those instances?

---

