---
title: "On Boot Drops to Busy Box How-To"
date: 2010-08-22
forum: General Help
---

### Post by th1bill on 2010-08-22
I've noted that this seems to be an issue with a lot of folks and the messages I've seen on screen run the gambit from ata3: [misc addresses] SRST failure to Kernal Panic.  I know bugs are filed so I'm not bothering but there is a magic fix!  Debian and Mepis use modul-assistant and on Meprislovers forum is where II learned about this easy repair.  Twice now, in a row, a header upgrade has broken my primary machine.

The repair is so easy you need only commit m-a, with no space, to memory.  Type that command into the terminal and it will give you the sudo command to install the module-assistant.  After installing it, again, type m-a and you'll et a very basic Graphic Menu.  Both times I have selected Prepare and hit enter.  When it finished I used the Down Key to select the next option, Upgrade, and when finished I rebooted with Zero errors.

Happy NIX Computing!

---

