---
title: "Cant start script automatically"
date: 2011-10-23
forum: General Help
---

### Post by jrohde on 2011-10-23
Hi

I want to have a script, GmoteServer.sh, start automatically every time I log on. If I start it manually in the terminal it works fine, but if I add it to the Startup Programs list, nothing happens.

Apart from the script file, there are two subfolders (bin and lib).

The script will start Gmote Server that naked it possible to remote control the pc using an Android phone. The will be no keyboard, so its not an option to start it manually.

Any suggestions?

/Jakob

---

### Post by hwttdz on 2011-10-23
You already put the full path in the startup program?

I'd also do 
/full/path/to/program > /home/user/Desktop/log.txt 2>&1

and then look at the log and see if there's any obvious funny business going on.

---

