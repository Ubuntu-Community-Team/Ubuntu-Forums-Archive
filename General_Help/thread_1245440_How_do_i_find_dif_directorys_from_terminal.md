---
title: "How do i find dif directorys from terminal?"
date: 2009-08-20
forum: General Help
---

### Post by masoud23 on 2009-08-20
Hello

i want to start lampp from terminal i can see that it is in: filesystem/opt/lampp  
 what is this in terminal? when i start the terminal i am in: 
masoud@masoud-desktop:~$ 
 where should i go fram here? how? i do not understand the structur, is filesystem blow or over the root or are they the same???

---

### Post by zkriesse on 2009-08-20
Go here. [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by s3a on 2009-08-20
I think you're asking about the *cd* command.

In your case, *cd /opt* then the *ls* command would show you lampp. I am not sure but maybe *./lampp* would run what you're trying to run? (Commands are in italics)

---

### Post by geirha on 2009-08-20
Nautilus's «filesystem» is the root directory, /, so the equivalent to «Filesystem -> opt -> lampp» is «cd /opt/lampp» in the terminal.

You can install lamp from the repositories btw, see chapters 9-11 in the server guide [https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

---

