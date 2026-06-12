---
title: "Startup script (delay?)"
date: 2011-03-20
forum: General Help
---

### Post by bill-lancaster on 2011-03-20
I have a script with a command that requires a network connection.
It worked fine with an ethernet connection but on changing to a wireless one, its stopped working.

Question:  how can I delay a script command until the network is connected?

Thanks

---

### Post by ajgreeny on 2011-03-20
Use a sleep option to the command, eg, in system ->preferences ->startup applications use the command ```
bash -c "sleep 10; script.sh"
```for a 10 second delay.  Use your own script name of course!

---

### Post by Krytarik on 2011-03-20
How did you set up the script to run?

---

