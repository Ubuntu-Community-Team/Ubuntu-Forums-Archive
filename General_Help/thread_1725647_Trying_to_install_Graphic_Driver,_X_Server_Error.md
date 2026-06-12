---
title: "Trying to install Graphic Driver, X Server Error"
date: 2011-04-10
forum: General Help
---

### Post by RB240 on 2011-04-10
I am trying to install NVIDIA graphics drivers. I can execute the .run but it comes up with an error the X Server is in use and needs to be closed.

I have tried to run

Ctrl Alt Backspace

and

sudo /etc/init.d/gdm stop

but the terminal requests the root password and I can not enter anything for the password in the line. If I go to the next line and enter anything the password fails.

Any suggestions?

---

### Post by mikewhatever on 2011-04-10
Use your user password, type it and hit enter. Note, there is no visual feedback when typing passwords in Terminal.

---

