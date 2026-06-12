---
title: "scripting woes"
date: 2010-06-08
forum: General Help
---

### Post by Scooter_X on 2010-06-08
I hope this is simple enough that I don't need to post it in the programming section...

I found out about syndaemon and love it, but I'm trying to make a script so I can run it on startup, but it doesn't seem to be working. Here's what I have so far:

```


sleep 15 &&
syndaemon -i -3 -d -t -K&
exit

```And it is executable. The 'sleep 15', the '&' symbols and 'exit' part are just something I chopped out of my script to run my dual-conky setup. I also tried:
```

sleep 15 &&
syndaemon -i -3 -d -t -K;

```because it's another script I used to use when I just did a single conky setup. Anyway, I'm totally trying to Frankenstein this together and it just ain't working. Can someone help me?

---

### Post by jbrown96 on 2010-06-08
You need ```
#!/bin/bash
``` at the beginning and it needs to be executable.

---

### Post by Scooter_X on 2010-06-08
Thanks.
Now my script is as follows:

```

#!/bin/bash

sleep 15 &&
syndaemon -i -3 -d -t -K&
exit
```and.... I STILL can't get it to work ](*,) Here's ls -l so that y'all don't think I'm crazy. It IS executable. :lolflag:

```
riley@satellite:~/scripts$ ls -l
total 48
-rw-r--r-- 1 riley riley  104 2010-05-28 16:29 battery.txt
-rw-r--r-- 1 riley riley 1773 2010-06-06 09:57 conky_weather
-rw-r--r-- 1 riley riley 1773 2010-06-06 09:57 conky_weather~
-rwxr-xr-x 1 riley riley  125 2010-06-08 21:18 dual_conky.sh
-rw-r--r-- 1 riley riley  125 2010-06-08 21:18 dual_conky.sh~
-rw-r--r-- 1 riley riley 6813 2010-06-06 08:25 rings.lua
-rw-r--r-- 1 riley riley 6813 2010-06-06 08:24 rings.lua~
-rwxr-xr-x 1 riley riley   56 2010-06-08 21:11 syndaemon.sh
-rw-r--r-- 1 riley riley   56 2010-06-08 21:10 syndaemon.sh~
-rw-r--r-- 1 riley riley  983 2010-05-28 16:29 wireless.txt
riley@satellite:~/scripts$ 
```I don't understand what the '#!/bin/bash' does for me though, because if it's preceded by a # then it's commented out, right?

Edit: nevermind, it's called a 'shebang' and I need it so the computer recognizes it as an executable script

---

### Post by Scooter_X on 2010-06-09
Dangit, I figured it out. Don't put the time in seconds as an option:

```
-3
```It's not an option, it's part of the -i option. Now it works. Thanks again, jbrown96 for showing me what I was missing. I appreciate it.

Therefore my code should be:

#!/bin/bash

sleep 15 &&
syndaemon -i 3 -d -t -K&
exit

---

### Post by Scooter_X on 2010-06-14
Well, I have found a solution to my problem. First of all, I remembered that I had downloaded 2 useless programs from the repository that were supposed to fix the issue. But they didn't work. I left them installed, then tried messing around with syndaemon and my script. 

The other thing I realized was that the only way I was able to get my script to work (while the 2 useless programs were installed) through the terminal was like this:
```

killall syndaemon; syndaemon -options
```I then modded my script to make it look like the code above, AND removed the useless programs, because I suspected they were trying to use syndaemon. The thing is, that syndaemon needs to be killed before you can go modding any options. So, I make sure that syndaemon is dead before trying to run it the way I want it to be ran. I could try just the script I was doing before now that the programs are gone, but I just remembered about this thread here @ work and don't have my computer with me so can't try. But anyway, if anyone wants to know what I did, here you have it. 

I guess this sortof went from general to specific... Oh well.

---

