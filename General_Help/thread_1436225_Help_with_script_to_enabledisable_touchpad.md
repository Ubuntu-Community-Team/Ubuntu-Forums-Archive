---
title: "Help with script to enable/disable touchpad"
date: 2010-03-22
forum: General Help
---

### Post by cbecker78 on 2010-03-22
Hi all.  I am able to get my touchpad to enable disable from the bash shell using
```

sudo modprobe -r psmouse
```with or without the "-r" to turn it on or off, respectively

But I wanted to write a script to do this for me because "mouseon" and "mouseoff" is easier for me to remember and more convienient...

But I am having some issues (I am a complete newb at scripting, so forgive my ignorance)

the script written is:
```
#!/bin/bash
#enable/disable touchpad

sudo modprobe -r psmouse
```I have saved this script as "mouseoff" in usr/bin (echo $PATH told me this was a directory bash searches, even though it was not a directory and I had to create it with mkdir).

then I did```
chmod 755 mouseoff
```However, when I try to run it, I get a "permission denied" error... 

Can anyone help me with what I am doing wrong?

---

### Post by Johnny B on 2010-03-22
you need to make it executable with
$ chmod +x mouseoff

---

### Post by cbecker78 on 2010-03-22
I thought that was what I was doing with chmod 755...  But since you didn't see a problem with the script, that made me think harder.  I was putting the script in to "myusername"/bin... I thought "usr" was supposed to just be generic for the username I log in with.  there is actually a "usr/bin" file, and putting it here and doing the chmod +x bit works!

Thanks so much!

---

### Post by wilee-nilee on 2010-03-22
fn-f7 will stop and start a pad.

---

### Post by cbecker78 on 2010-03-22
> **wilee-nilee said:**
> fn-f7 will stop and start a pad.

On my laptop, it's actually supposed to be fn F9, and fn F7 and F8 controll brightness.  However, none of these fn key work with ubuntu installed.  I found the "sudo modprob" workaround here on the forums and was happy to get it too a script I could activate w/o having to mouse around. :)

---

### Post by ochoadavid on 2010-11-04
Hi! 

This tread is marked as solved but I developed a script for disable/enable the touchpad. Maybe is useful for someone. Has the advantage of not needing administrator privileges (sudo).

```

#!/bin/bash

A=`xinput list-props "SynPS/2 Synaptics TouchPad" | sed -n -e 's/.*Device Enabled (121):\t\(.*\)/\1/p' `

if [ $A -eq 1 ]; then
      xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Device Enabled" 8 0
else
      xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Device Enabled" 8 1
fi

```

David

---

### Post by UburR00T on 2011-07-14
Thanks a lot David, just what I was looking for :)

---

