---
title: "Run Menu Programs as Root By Default"
date: 2011-03-01
forum: General Help
---

### Post by nova47 on 2011-03-01
In the applications menu I would like to always run certain programs as root. For instance Wireshark; I'll never want to run that as a regular user I'll always want to be root. Is there a way to set it up so that when I click it in the menu I'm prompted for my password and it will automatically run as root? (Much like in windows you can right click and check the box that says always run as administrator.)

---

### Post by marshmallow1304 on 2011-03-01
Right-click the menu and click "Edit menus", find the entry you want to change, click edit, and then add gksudo in the command box in front of the existing command.

---

### Post by nova47 on 2011-03-01
Perfect, thanks so much. I knew there had to be a way to do it couldn't find it anywhere on google.

---

