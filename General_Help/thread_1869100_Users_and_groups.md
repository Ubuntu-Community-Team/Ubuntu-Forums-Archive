---
title: "Users and groups"
date: 2011-10-25
forum: General Help
---

### Post by Gwaro on 2011-10-25
I am unable to add myself to Virtual-box users in Ubuntu 11.10. I don't even know how to go about this! I guess many things have changed here.

---

### Post by matt_symes on 2011-10-25
Hi

You can do it from a terminal. Open a terminal and type

```
sudo usermod -a -G <virtual_box_group_name>
```

Change <virtual_box_group_name> to the virtual box group name. 

Enter your password. It will not be echoed to the screen.

Kind regards

---

