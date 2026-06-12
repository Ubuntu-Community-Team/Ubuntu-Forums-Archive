---
title: "xgl login problem"
date: 2006-06-27
forum: General Help
---

### Post by ryanthelaxer on 2006-06-27
hello all, i am running 32-bit ubuntu 6.06 and wanted to install xgl/compiz.  i started with this site:

 [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

i followed the directions to a t! but when i choose options -> session manager -> xgl from the login screen, and then attempt to log in, i get an error message saying that my gnome session lasted less than 10 seconds and there is an error... here is what the error dialog read:


   /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

   /etc/gdm/PreSession/Default: running:/isr/bin/sessreg -a -w /rar/log/wtmp -u                            
   /rar/run/utmp -x "/rar/lib/gdm/:0.Xservers" -h "" -l ":0" "ryan"

   /etc/gdm/Xsession: Beginning session setup...

   sleep: missing operand

   Try 'sleep --help' for more information

   /usr/bin/startxgl.sh: line 3: 2: command not found

im not sure how to fix this ](*,)  any ideas??
 thanks in advance!

---

### Post by ryanthelaxer on 2006-06-27
it turns out i cant read my own writing... replace all those /rar... with /var

oops

---

### Post by cbudden on 2006-06-27
Can you log into a normal gnome session and paste the output of this here:

```

cat /usr/bin/startxgl.sh

```

Thanks

---

### Post by ryanthelaxer on 2006-06-27
here ya go:

#!/bin/bash
Xgl -fullscreen :0 -ac -br -accel glx:pbuffer -accel xv:fbo & sleep
2 && DISPLAY=:0 gnome-session

now that i look at it... do i need an integer after sleep? or is there some other problem?

---

### Post by ryanthelaxer on 2006-06-27
that goofy face :p is actually a ": p" without the space in the script

---

### Post by cbudden on 2006-06-27
Is that all on one line  ? ( if you drag your terminal wider and then issue the command you'll see if it prints one line or two).

---

### Post by ryanthelaxer on 2006-06-27
cbudden youre a freakin stud!!
it was on 2 seperate lines
so that "2" on the 3rd line is the argument for "sleep"

i put the last two lines together and i am now sending this message from inside the xgl login.

thanks a ton!!
now its time to get compiz running8)

---

### Post by cbudden on 2006-06-27
That is good news, glad your all up and running :)  Getting compiz running is easy peasy once you have XGL running.  There are plenty of scripts around to do it.  I use one that has a notification area icon which allows me to right click and switch to metacity, restart compiz or run gset-compiz.

If you want, the files are attached.

Copy compiz-start.py to /usr/local/bin, then copy the image to /usr/share/compiz/logo24.png

```

sudo cp compiz-start.py /usr/local/bin/compiz-start.py

sudo cp logo24.png /usr/share/compiz/logo24.png

```

Once you have done that add compiz-start.py in system-prefs-sessions on the startup programs tab.

---

### Post by Tylo on 2006-06-27
I am having a similar problem to his. Instead of getting error messages though, the splash screen just goes away, the cursor icon appears to be loading something, then my monitor power-flickers and I am back at the splash login screen.

This is what my startxgl.sh looks like:
```
#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 gnome-session

```

---

### Post by Tylo on 2006-06-29
Can anyone help me with my problem? I have an ATI Radeon 9600 AIW. So far all steps have worked fine in the [wiki to install this feature.]("https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28XGL%29") I did method A for attempting to start XGL.

I throw myself at the mercy of the community!

---

