---
title: "cron, run-parts, and python"
date: 2006-03-24
forum: General Help
---

### Post by Lutz Mueller on 2006-03-24
Greetings,

I found out today that my python scripts don't execute out of /etc/cron.hourly anymore (they used to).

run-parts --test /etc/cron.hourly   returns *nothing*, whereas
run-parts --test /etc/cron.daily     prints the expected list of (non python) shell scripts.

All my python scripts are executable, I can call them manually (./myscript.py). I am using #! /usr/bin/env python as my first line in every script.

I have renamed a shell script so that it has the extension .py, and it
will no longer be printed by run-parts --test.

Now, to the best of my knowledge, I didn't change anything. Could someone please give me an idea where to look? It's almost as if run-parts doesn't like python scripts anymore...

Thanks for your time !

Best Regards,

Lutz

---

### Post by matthinckley on 2006-03-24
I found the easiest way for me to manage my cron tasks was to create my own crontab using 
```
crontab -e
```
or to run the tasks as root
```
sudo crontab -e
``` 
instead of putting the scripts into the cron.daily, etc.. directories.

It may not be seeing your scripts that end in .py but with your own crontabe entry you actually put in they location of your scripts so you could put in
```
5 * * * * /home/user/cron/script.py
```
to run your script every hour at 5 after.

I'm not sure if this would fix your problem, as I'm kindof a newb myself but you might try it

Matt

---

### Post by Lutz Mueller on 2006-03-24
Thanks for the quick reply.

I'm sure it would work this way, but you are losing the convenience of just dropping scripts in their respective cron directory.

Plus, it doesn't really get to the core of the problem, which is why run-parts would not even see the .py scripts anymore.

Thinking back, the only thing I recall really changing is going from a 386 kernel to a 686...

I'd really be glad if I could get to the bottom of this.


Lutz

---

### Post by Lutz Mueller on 2006-03-28
Anyone? :-)

Lutz

---

### Post by mariohelmet on 2007-02-05
Try removing the extention py from myscript.py. You can also create a symbolic link (without extention) to your file (with extention)

---

### Post by david.hilton.p on 2008-03-07
gnuru.org/article/952/cron-run-parts-script-names

run-parts doesn't process scripts that have names that include "."s, among other things.

---

