---
title: "alltray from a script"
date: 2010-06-16
forum: General Help
---

### Post by WiiTard on 2010-06-16
Hello all.

I'm having an issue with a startup script that I wrote. I'm using Alltray to dock Thunderbird to my panel next to the clock.

I wrote a simple bash script to accomplish this:

```

#!/bin/bash

exec alltray thunderbird &

```I put this script in /etc/network/if-up.d   because I want it to automatically launch Thunderbird in docked mode as soon as my computer connects to the Internet. I can manually run this script just fine, but the system will not launch AllTray

I already chmodded the file, so it has permission to be executed. But for some reason it will not launch. I know that the system is actually running the script because I had it echo "Hello World" to a text file on the desktop. But it won't run any programs.


Any help is greatly appreciated!

---

### Post by yeleek on 2010-06-16
Tried specifying the path to thunderbird?

---

### Post by wilee-nilee on 2010-06-16
In startup application if you put alltray thunderbird in the command that will work if the script doesn't.

---

### Post by WiiTard on 2010-06-16
> **yeleek said:**
> Tried specifying the path to thunderbird?
Well in the script I tried
```

#!/bin/bash

exec alltray /usr/bin/thunderbird &

```

But it did not work.

> **wilee-nilee said:**
> In startup application if you put alltray  thunderbird in the command that will work if the script doesn't.

I had originally done this, but I don't want it to start until I'm connected to my wi-fi connection. 

Putting it in startup applications will launch Cometbird before Ubuntu connects to my wifi, and an annoying pop up box will come up saying Imap server not found.

---

### Post by yeleek on 2010-06-17
Ok - don't know why its not working there...

but how about writing a script that checks if it can ping its default gateway, if it can launch thunderbird.  Then put that as a startup app?

Half way there for you - something like this
[http://www.brendangregg.com/ping_scripts.html](http://www.brendangregg.com/ping_scripts.html)

---

### Post by omegaFil on 2011-03-02
I know it's a six month' old thread and I apologize for re-opening discussion...  :roll:

but did you check if Alltray is installed?
Try executing your command from a terminal and check output.

Cheers

---

