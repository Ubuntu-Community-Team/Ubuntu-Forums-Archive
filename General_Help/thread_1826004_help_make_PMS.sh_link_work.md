---
title: "help make PMS.sh link work"
date: 2011-08-16
forum: General Help
---

### Post by surfmonkee on 2011-08-16
fujitsu laptop, ps3 media server installed and working fine.

I have a folder 'pms linux 1.20.412' in my downloads folder. when i double click PMS.sh to run, it opens a dialogue asking what to do, i click run, it runs. 

amazing software streaming to my bravia and my ps3:)

i want to add this program to my applications menu or at least a link on the desktop.

i made a link, put it on the desktop but when i click it, it wont run, if i click the link properties it is checked to run as executable but still fails to actually run.

If i go back to the pms.sh in thedownloads/pms-linux and click it, it works fine

can anyone help me to make a desktop shortcut work as i dont want to have to navigate through folders each time i want to run it, 

i also dont want it to run on every start up (which it does not atm but i also dont want that advice, just advice to make a shortcut work)

 thanks

---

### Post by Habitual on 2011-08-16
make a .sh file with these contents:
```
#!/bin/bash
~/thedownloads/pms-linux/pms.sh
```

save it, as say ~/pmsstart.sh

Open terminal > 
```
chmod 700 ~/pmsstart.sh
```

Create a new desktop launcher pointing to ~/pmsstart.sh

Done.

---

