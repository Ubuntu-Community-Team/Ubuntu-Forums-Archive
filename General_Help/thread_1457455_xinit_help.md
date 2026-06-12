---
title: "xinit help"
date: 2010-04-18
forum: General Help
---

### Post by forshee on 2010-04-18
I'm running 9.10 and have the gdm disabled and I'm trying to run a single program from an upstart boot script. I'm fairly sure that the upstart script is ok unless I need something more than "exec xinit *my_client*" in the body. It seems like the program starts and crashes instantly when its run from script even though it runs fine from the terminal. When I explicitly specify xterm as the client it seems to open xterm again and again until it crashes.  Any one know what my issue is?

---

### Post by N.Simpson on 2010-05-26
> **forshee said:**
> I'm running 9.10 and have the gdm disabled and I'm trying to run a single program from an upstart boot script. I'm fairly sure that the upstart script is ok unless I need something more than "exec xinit *my_client*" in the body. It seems like the program starts and crashes instantly when its run from script even though it runs fine from the terminal. When I explicitly specify xterm as the client it seems to open xterm again and again until it crashes.  Any one know what my issue is?

This might not be your issue but if you are trying to run xinit as a non-root user then you could try [http://malovo.com/xinit/starting-x-non-root-user-ubuntu-server-1004-lucid-lynx-using-upstart](http://malovo.com/xinit/starting-x-non-root-user-ubuntu-server-1004-lucid-lynx-using-upstart).

---

