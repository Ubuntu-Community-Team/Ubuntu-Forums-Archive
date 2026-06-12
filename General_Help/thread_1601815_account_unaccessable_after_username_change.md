---
title: "account unaccessable after username change"
date: 2010-10-20
forum: General Help
---

### Post by zarathustra@ on 2010-10-20
i followed the instructions in [http://ubuntuforums.org/showpost.php?p=7958725&postcount=11](http://ubuntuforums.org/showpost.php?p=7958725&postcount=11)
result was that my pc is rendered unusable. i have no graphical interface when logging in. i can call only the terminal. 
some of the error msgs i got were, for example : Nautilus can't create' Desktop and .nautilus folders in /home/ 'new_username/ . there were more error msgs.
i have a terminal with the new username before the bash command line, but the user_folder in home is still the  old_username. 

my mistake was, as i discovered later, is that i followed the instructions **_not_** in recovery mode.

question is, how can i make it all right again, and make my ubuntu to function normally again?

---

### Post by terdon on 2010-10-21
Hi, well, this should be fun :)

OK, first of all if I understand correctly there is no /home/new_username/ folder. If that is the case your problems may be quite simple to solve. What username do you use to log in?

In any case, once you log in issue the following commands:```

sudo mkdir /home/new_username
sudo chown new_username /home/new_username
sudo chgrp new_username /home/new_username
sudo service gdm restart
```

If all went well you will now be back at the graphical login screen. Try logging in with the new username. Let me know how it goes.

---

### Post by zarathustra@ on 2010-10-23
Thank for your reply!

i managed to solve the problem by repeating the steps instructed in the link, only now i used the old name in place of the new, and the new username in place of the old.
this way, i turned things back to the state they were before.

your solution sounds logical to me. since i didnt knew all the necessary syntax to associate the directory (saw your reply after i solved it) to the user i decided to undo all changes.

thanks again!

---

### Post by terdon on 2010-10-23
You are very welcome, glad it's sorted

---

