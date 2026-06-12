---
title: "Help: Need to Control a Script"
date: 2011-02-04
forum: General Help
---

### Post by Sugi on 2011-02-04
I have another question about scripts, let's say I wanted to restart an application when it shuts down, but in this same fashion. This would be the correct script for it right? I have it shutting down all calculators and then restart them. So, if I close it down or if it crashes. It will repeat the whole process right?

```

#!/bin/bash
while [ 1 ]
do
	killall -9 gcalctool
	sleep 5
	gcalctool
	sleep 5
done
```


**Updated:**
Hello everyone, I need to make a test bash script, though I got it working and to loop it's self forever, but I would like to control the script from the terminal and have it not be depended on the terminal window it's self. 

Want: Be able to pause script.  See the progress of the script.
Do not want: close terminal window, stop script.

Is this possible?
```

#!/bin/bash
echo Hello Mr. Sugi.
sleep 3
bash /home/sugi/test.bash
```

Fix 1:
screen bash ~/test.bash

How To Install, Create/Detach And Kill Screen Processes In Linux:
[http://linuxchunks.com/2010/10/how-to-install-createdetach-and-kill-screen-processes-in-linux/](http://linuxchunks.com/2010/10/how-to-install-createdetach-and-kill-screen-processes-in-linux/)

Linux Tutorial & Howto:
[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

Ubuntu 10.10 x64
Sugi

---

### Post by papibe on 2011-02-04
Is this your script?
```
#!/bin/bash
echo Hello Mr. Sugi.
sleep 3
bash /home/sugi/test.bash
```
If it is, it's a very bad idea since it'll generate an infinite calling and eventually eats all your memory (very slowly though).

Change it for something like:
```
#!/bin/bash
while [ 1 ]
do
    echo Hello Mr. Sugi.
    sleep 3
done

```
Anyway, you can use screen to make it independent of the terminal. Something like this:
```
$ screen /home/sugi/test.bash
```
To disconnect from the screen press ctrl-a d. To get into the screen again run:
```
% screen -r
```
You can get more info about screen in its manual or by google "screen tutorial".

I hope it helps.

---

### Post by HermanAB on 2011-02-04
Howdy,

Read up on 'Linux job control'.

---

### Post by Sugi on 2011-02-04
How do I turn off the screen that is currently running when it is detached?

Fix:
ps –ef | grep screen
kill XXXX
[http://linuxchunks.com/2010/10/how-to-install-createdetach-and-kill-screen-processes-in-linux/](http://linuxchunks.com/2010/10/how-to-install-createdetach-and-kill-screen-processes-in-linux/)

Thanks for the information on screens.  Very useful!

Edit:
I have another question about scripts, let's say I wanted to restart an application when it shuts down, but in this same fashion.  This would be the correct script for it right?  I have it shutting down all calculators and then restart them. So, if I close it down or if it crashes. It will repeat the whole process right?

```
#!/bin/bash
while [ 1 ]
do
	killall -9 gcalctool
	sleep 5
	gcalctool
	sleep 5
done 
```

Sugi

---

### Post by papibe on 2011-02-04
> **Sugi said:**
> How do I turn off the screen that is currently running when it is detached?

Attach the screen, cancel the script, and exit bash:
```
$ screen -r
Hello Mr. Sugi.
Hello Mr. Sugi.
Hello Mr. Sugi.
^C
$ exit
```
I hope it helps.

---

### Post by Sugi on 2011-02-06
Bump.

Sugi

---

### Post by asmoore82 on 2011-02-06
I'm confused on what you are trying to accomplish.

You should only `kill -9` when absolutely necessary. You should always
try a plain `kill` first to give the App a chance to die gracefully.

---

### Post by Sugi on 2011-02-06
asmoore82,
I would like to make a script, to first check for an application status, if it is frozen or shut down, then secondly, terminate the application, and then thirdly start it back up.  Then finally repeat the whole process.  If the application is working correctly, then it shouldn't trigger the next commands, but wait until the application is failing to start the next triggers.  So, this script becomes a failsafe to get the application back online when something goes wrong.  I don't mind changing the kill command at all.  Is it possible to make such a script though?

Sugi

---

### Post by Sugi on 2011-02-07
Bump this thread.

Sugi

---

### Post by asmoore82 on 2011-02-07
It is notoriously difficult, maybe impossible, to truly determine when a program is frozen.
The problem is that "working extremely hard" looks identical to frozen - and
"working extremely hard" is the *worst possible* time to kill an application that isn't misbehaving.

I've seen Gnome, Compiz and other OS's mis-flag Apps as "Not Responding" far
too many times. And I wouldn't want to get too philosophical, but wouldn't
it be more productive to investigate and bugreport the frozen App?

---

