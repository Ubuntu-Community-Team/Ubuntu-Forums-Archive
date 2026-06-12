---
title: "Uninstall Ubuntu under Wubi But there's a problem"
date: 2009-09-13
forum: General Help
---

### Post by volkova on 2009-09-13
I am using Wubi to intall Ubuntu and i am glad for the great experience but recently i want to try something and uninstall everything again (so that i can install it again ^O^ sounds stupid)


now i uninstall ubuntu using windows xp in the add remove programs and it goes well so fast nothing bad happens but when i tried to restart my pc the ubuntu partition was still there and the pc is still in dual boot mode why is this?

uhm everything is fine but i just want to know why there is still two os boot why i restart my pc and how to get rid of it please provide me with a step by step procedure...

i am using a laptop and windows xp sp2 thank you

---

### Post by harrismh777 on 2009-09-13
hi,
I would like to encourage you to skip wubi and setup that machine as dual boot if you need to.  Shrink the windows partition, and install ubuntu along side... dual boot the machine into which-ever you need...   

Or even better... scratch the entire system and just install ubuntu !  Its do-able man... I haven't run windows now for, well, almost 10 years. Half of my systems are running opensuse, and half of them are now running ubuntu 9.04... and ALL of my desktops are now running ubuntu 9.04.

Just make the switch and get on with life... yes... there is life after windoze... truly.

---

### Post by rocket16 on 2009-09-13
[B][FONT="Comic Sans MS"]Hello. This problem occurs, since Ubuntu Wubi creates an option to boot Ubuntu in the boot.ini file in Windows XP. You should have to manually edit the Boot.ini file in Windows XP to setlle this Problem. To do this,
Click Start, click Run, type sysdm.cpl, and then click OK.
On the Advanced tab, click Settings under Startup and Recovery.
Under System Startup, click Edit. Now, remove the "Ubuntu" containing line, and you are done![/FONT][/B]

---

