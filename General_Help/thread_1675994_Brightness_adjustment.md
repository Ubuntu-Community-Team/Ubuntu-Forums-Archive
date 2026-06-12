---
title: "Brightness adjustment"
date: 2011-01-26
forum: General Help
---

### Post by nishant_1989 on 2011-01-26
Recently I installed Ubuntu 10.10 32-bit on my desktop. My monitor appears very bright. I am unable to find any brightness control tool in ubuntu. 
I tried installing Gnome color manager. In its help I found that fine tuning option is available in advanced preferences and to activate that GConf must be configured manually. The help states-

The Fine Tuning Option is only available if you configure GConf to enable it ( apps &#9656; gnome-color-manager &#9656; show-fine-tuning).

How can I do this? Also please suggest other methods of controlling brightness

---

### Post by Denis Dyakov on 2011-02-01
Use terminal, type and run "gconf-editor", open apps->gnome-color-manager, click show_fine_tuning. That's all :wink:

---

