---
title: "script request"
date: 2006-04-05
forum: General Help
---

### Post by moon_dog on 2006-04-05
can anyone create a script for turning transset on and off?  i mean, executing transset 0.65, then the next time the script is run, executing transset 1.  i was thinking of keybinding the script.  i know more or less how the script should go but i'm not familiar at all with the syntax.  i was thinking of something like

a=0;
if a=0 then
{ 
transset 0.65;
a=1;
}

else 
{
transset 1;
a=0;
}

that's just off the top of my head, and the syntax is probably wrong, since i haven't programmed anything in 5 years.  but that's the basic gist.  if anyone can come up with a script it would be great.  thanks.

---

### Post by schilcha on 2006-04-05
Try:
```

#!/bin/sh

# if the file /tmp/transset exists, use paramter 1 to transset
# otherwise use 0.65 for transset
CHECKFILE="/tmp/transset.status"
if [ -e $CHECKFILE ] 
then
  transset 1
  # rm the file, so next time 0.65 will be used
  /bin/rm $CHECKFILE
else
  transset 0.65
  # create the file, so next time 1 will be used
  touch $CHECKFILE
fi

```
This'll use the existence of a file instead of the variable "a" from your snipplet. That'll make sure, that the information survives until next time you execute the script.

Good Luck!

BTW: I haven't tried the code, hope it works anyways...

---

### Post by moon_dog on 2006-04-05
it works great, thanks.  is there some resource to learn linux scripting?

---

### Post by schilcha on 2006-04-05
There is for sure -- I simply don't know any.

I vaguely remember that there was a link to some website in a thread here somewhere, but I can't find it. 

Sorry.

---

