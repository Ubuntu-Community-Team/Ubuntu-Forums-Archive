---
title: "Hang on panic. Even with panic=20 boot option."
date: 2011-09-26
forum: General Help
---

### Post by Wombat2k on 2011-09-26
[FONT=Fixedsys]I want Ubuntu to restart on a kernel panic after 20 seconds.
I`ve added panic=20 to boot options and added kernel.panic = 20 to [/FONT][I][FONT=Fixedsys]/etc/sysctl.conf.
When I cause a panic from a terminal within X the user interface freezes and thekeyboard lights don`t flash. 
From  a console (ctrl + alt + F1-F6) inducing a panic causes ubuntu to reboot as requested. 
How can I make sure that ubuntu recovers from a panic even if it happens within X?
[/FONT][/I]

---

