---
title: "Loading/unloading modules in /etc/modules bttv"
date: 2009-10-24
forum: General Help
---

### Post by Hugh Mulqueen on 2009-10-24
I dont want to enter the following at every time i turn on my computer:

[B]sudo rmmod bttv
sudo modprobe bttv card=10 tuner=55[/B]

So i need help to stop bttv module being automatically loaded at startup and then reloaded with my specs above. 

I have been trying and failing to edit /etc/modules for hours.

Any suggestions would be much appreciated,

Thanks.

---

### Post by VirtualFab on 2009-11-04
You just have to create a new text file in /etc/modprobe.d, calling it bttv.conf or something like that, and put your options in it, like these:
```

options bttv card=10 
options tuner=55

```
This should resolve your issue.
If you want to have a more verbose logging (in syslog) you could append a ```
bttv_verbose=2
``` to the bttv options line.

Ciao.

> **Hugh Mulqueen said:**
> I dont want to enter the following at every time i turn on my computer:

[B]sudo rmmod bttv
sudo modprobe bttv card=10 tuner=55[/B]

So i need help to stop bttv module being automatically loaded at startup and then reloaded with my specs above. 

I have been trying and failing to edit /etc/modules for hours.

Any suggestions would be much appreciated,

Thanks.

---

### Post by Hugh Mulqueen on 2009-11-05
Thanks very much for the reply. One problem though i did what you said and got this as the output:

```
WARNING: /etc/modprobe.d/bttv.conf line 2: ignoring bad line starting with 'options'
```

So all I did was delete the second line and add the following:

```
options bttv card=10 tuner=55
```

It worked like a charm,;) thanks very much now I can watch all the TV I want..:popcorn:

---

### Post by lupin492 on 2010-01-31
I found exactly the same problem after a fresh re-install of Ubuntu 9.10. Having found this post, I was able to solve the problem of options being passed correctly to the module, the same way Hugh Mulqueen did (only one line of options).
But now it made apparent that I was having two problems, not just one.
The first time I start a TV app (TVTIME or XAWTV) it shows a blank window (black).  When started from a terminal, it shows a couple times:

videoinput: Can't free frame 1: Argumento inválido
videoinput: Can't free frame 2: Argumento inválido
videoinput: Can't free frame 3: Argumento inválido

and it refuses to close from the window's own controls.  Even forcing it to do so with Xkill, it will leave the process behind, and I'll have to kill it from a command line.

If I close this instance of the app and start it again, it works fine...why?

Please does somebody figure out what could this be due to ?
Thanks in advance ! Regards,

---

### Post by Hugh Mulqueen on 2010-03-09
My Spanish(/or is it Italian? :P ) isn't great but a you could have just entered in the wrong argument (ie. the wrong numbers). 

[PHP]videoinput: Can't free frame 1: Argumento inválido
videoinput: Can't free frame 2: Argumento inválido
videoinput: Can't free frame 3: Argumento inválido
[/PHP]
What you should do is try to find out your own numbers for the card you are using...

I have a complete tutorial on how to correct the problem here:

[URL="http://ubuntuforums.org/showthread.php?t=1319187"]http://ubuntuforums.org/showthread.php?t=1319187
[/URL]

If you have any problems don't hesitate to contact me. 

good luck!!

---

