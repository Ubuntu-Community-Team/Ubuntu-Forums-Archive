---
title: "Automatix - winecfg: command not found"
date: 2006-03-26
forum: General Help
---

### Post by Soviet on 2006-03-26
I installed a bunch of packages using Automatix, including wine. I tried to run winecfg and it says it's not a command. I tried isntalling Wine once again, just now, from Automatix. Still nothing.

Anyone know how I can get it to work?

---

### Post by s_h_a_d_o_w_s on 2006-03-26
I installed Wine with automatix. when i type winecfg in terminal, i just waited like 5 seconds and it popped up. maybe type winecfg and wait 30 secs.

---

### Post by Sutekh on 2006-03-26
Here's how I'd install wine, it's not hard, and you can learn some more about Linux :)

 - Open a terminal window (from the Menu; Applications -> Accesories -> Terminal), and issue the commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo nano /etc/apt/sources.list
``` - This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

- To install wine you will need the wine repository; add these lines to your sources.list
```

deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
``` - Then save the file (Ctrl+O) and exit (Ctrl+X).

 - Update the repositories using
```
sudo apt-get update
```

 - Finally you can install wine using
```
sudo apt-get install wine
```

 - Then you can run **winecfg**

---

### Post by arnieboy on 2006-03-26
[QUOTE=Soviet]I installed a bunch of packages using Automatix, including wine. I tried to run winecfg and it says it's not a command. I tried isntalling Wine once again, just now, from Automatix. Still nothing.

Anyone know how I can get it to work?[/QUOTE]
the reason behind that is because the official wine repositories get awfully slow at times and the wine package does not get completely downloaded at one go.
here is what u can do:
from terminal simply do:
```
sudo apt-get install wine
```
it will start downloading from where it left off if it indeed was incomplete. Keep repeating the same till the file gets downloaded and installed finally.
after that run
```
winecfg
```

---

