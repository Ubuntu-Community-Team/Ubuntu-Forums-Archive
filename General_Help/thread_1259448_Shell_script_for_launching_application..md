---
title: "Shell script for launching application."
date: 2009-09-06
forum: General Help
---

### Post by pwicken on 2009-09-06
I am totally ignorant in linux shell scripting.

My problem is that I have been putting together an old PC for the daughter of a friend. It has an Intel integrated video card (82865G). After installing version 2.4 of the Intel Xorg video driver it runs pretty well with compiz except for Google-Earth. 

Thus, I would like to make a shell script that does something like this:

metacity --replace
exec googleearth
On GoogleEarth close
compiz --replace
emerald --replace 

Any help would be highly appreciated.

---

### Post by lovinglinux on 2009-09-06
```
#!/bin/bash

metacity --replace
googleearth &&
compiz --replace
emerald --replace 
```

---

### Post by Brandon Williams on 2009-09-06
The shell script will essentially be a listing of the commands that you would enter on the command line if you were carrying out the operations by hand. So, if all the commands you listed are exactly what you want to run, then your script would look like this:
```
#!/bin/bash
metacity --replace
googleearth
compiz --replace
emerald --replace
```
The first line is required to tell the kernel which interpretter to use when running your script. Also, note that I've remove the 'exec' in front of the command googleearth, since that would cause your script to stop running and be replaced by googleearth entirely, which means that the remaining two lines would not be run after googleearth exits.

I don't use compiz or emerald, so I don't know whether the metacity, compiz, and emerald commands you've listed will exit immediately. I've assumed that they do. The script will require some changes if that's not the case.

---

### Post by pwicken on 2009-09-06
Thanks, I have tried along these paths, quite unsuccessfully. 

When I run the script of lovinglinux it executes the first line and nothing more happens... until I enter Alt-F2 "compiz --replace" then the script continues and launches googleearth. But, alas now compiz in active and nothing is gained.

Brandon's script is exactly what I tried initially and gives about the same result.

I have also tried gamestart.sh
[http://ubuntuforums.org/archive/index.php/t-518227.html](http://ubuntuforums.org/archive/index.php/t-518227.html)
No success...

However if I try to repeat metacity --replace googleearth will launch in metacity
```

#!/bin/bash
metacity --replace
metacity --replace
googleearth
compiz --replace
emerald --replace
```

However, once I exit googleearth and the script correctly returns to compiz it launches a new instance of googleearth now under compiz.

Having to enter one command twice in order to execute the next is rather messy so this is probably not the way to go.

---

### Post by Brandon Williams on 2009-09-06
If you open a terminal and run that list of commands in that order at the command prompt, does it do what you want? If so, then it's possible that the system requires a little bit of delay in between the commands, since it probably takes you a few seconds to get the next command line typed in after the previous one completes.

Run 'metacity --replace' and wait for all effects of the command to be completed. How long did it take? Try addin a call to sleep in between the metacity command and the googleearth command to give metacity a chance to finish initialization.

---

### Post by lovinglinux on 2009-09-06
Try this:

```

#!/bin/bash

metacity --replace &
sleep 5 &&
googleearth &&
emerald --replace &
```

Don't remove the second blank line, since it's required for the script to work properly. Also don't remove the && symbols. They are there so the next command doesn't start until you close googleearth.

---

### Post by unutbu on 2009-09-06
[PHP]#!/bin/bash
metacity --replace &
googleearth
emerald --replace &
[/PHP]

"metacity --replace" needs to be run in the background so that the script proceeds to the googleearth command.

---

### Post by lovinglinux on 2009-09-06
> **unutbu said:**
> [PHP]#!/bin/bash
metacity --replace &
googleearth
compiz --replace &
emerald --replace &

[/PHP]

Oops. You are right. I forgot about the single ampersands. It doesn't work without them, since metacity needs to be sent to the background, otherwise googlearth won't execute while metacity is running. 

I suggest this:

```

#!/bin/bash

metacity --replace &
sleep 5 &&
googleearth &&
emerald --replace &
```

---

### Post by pwicken on 2009-09-06
Thank you, That's perfect.

---

