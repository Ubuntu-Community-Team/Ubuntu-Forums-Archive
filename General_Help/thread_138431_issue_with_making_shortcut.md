---
title: "issue with making shortcut?"
date: 2006-03-01
forum: General Help
---

### Post by Trab on 2006-03-01
hey ya'll, i just got a CS server set up on my machine, it works fine, i can connect and play...
but i cant make any shortcuts to it!
the command i run from the command line is
```

./hlds_run -console -game cstrike -insecure -port 27001 +maxplayers 10 +map cs_militia -autoupdate

```
this HAS to be run from the /home/user/CSds folder tho (where i installed everything to) and it works fine..
but running
```

 /home/user/CSds/hlds_run -console -game cstrike -insecure -port 27001 +maxplayers 10 +map cs_militia -autoupdate 

```
it says 'Invalid game type 'cstrike' sepecified.'

because of this, i cant make a panel shortcut (as far as i know...) they all give the same error!

any help would be apprecated...
thanks
-Trab

---

### Post by seankann on 2006-03-01
Make a shell script to run it

goto your home dir

nano -w cs-server <enter>

In there type 

cd /home/user/Csds
./hlds_run -console -game cstrike -insecure -port 27001 +maxplayers 10 +map cs_militia -autoupdate

hit Ctrl+W then hit enter
 
That will save it

Then make a short cut on your desktop don't remember the tab but there will be one that will say run in terminal

Put in sh /home/user/cs-server

Then when you double/single click it, it will open in a terminal then run your command

That should work.

If it doesn't let me know what it's doing

---

