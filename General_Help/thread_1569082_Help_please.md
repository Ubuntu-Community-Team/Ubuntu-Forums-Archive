---
title: "Help please"
date: 2010-09-06
forum: General Help
---

### Post by farouk2506 on 2010-09-06
HI every one,
i am really new on GNU/linux, i switches to the OS two weeks ago just to  be able to use a software dedicated for robotcs use, i finally managed  to install the software although it wasn't straight forward for me, the  link to every think about the software is:
[http://asl.epfl.ch/~fpont/genom/]("http://asl.epfl.ch/%7Efpont/genom/")
My problem is that i have forgotten to configure my system before and i  can't figure out what are the commands to do so, i will give you the  CONFIGURATION paragraph from the User Manual so that you might give me  the commands:
----------------------------------------------------------
1.3 Conguration
You will need to specify a root path (for instance the environment variable
OPENROBOTS) where
the binaries, the libraries, the include les, and so on will be installed. Typically you can set
this environment variable to
/usr/local/openrobots.
Then modify (or set if not previously dened) the following environment variables :
PATH : add $OPENROBOTS/bin
PKG_CONFIG_PATH : add $OPENROBOTS/lib/pkgconfig
LD_LIBRARY_PATH : add $OPENROBOTS/lib:$OPENROBOTS/lib/openprs
--------------------------------------------------------
HEEEEEELP PLEASE.

---

### Post by The Cog on 2010-09-06
I'm guessing a script something like this might do the trick:
```
export OPENROBOTS=/usr/local/openrobots
export PATH="$OPENROBOTS":$PATH
export PKG_CONFIG_PATH="$OPENROBOTS"/lib/pkgconfig:$PKG_CONFIG_PATH
export LD_LIBRARY_PATH="$OPENROBOTS"/lib/openprs:$LD_LIBRARY_PATH
"$OPENROBOTS"/openrobots
```

---

### Post by farouk2506 on 2010-09-06
hi THE TOG,,,
I'm afraid it's still not working,this is what i got from the terminal after typing what you gave me:--------------------------------------------------
root@farouk-laptop:~# export OPENROBOTS=/usr/local/openrobots
root@farouk-laptop:~# export PATH="$OPENROBOTS":$PATH
root@farouk-laptop:~# export PKG_CONFIG_PATH="$OPENROBOTS"/lib/pkgconfig:$PKG_CONFIG_PATH
root@farouk-laptop:~# export LD_LIBRARY_PATH="$OPENROBOTS"/lib/openprs:$LD_LIBRARY_PATH
root@farouk-laptop:~# "$OPENROBOTS"/openrobots
bash: /usr/local/openrobots/openrobots: No such file or directory
-------------------------------------------------------------------
can you find where the problem is?

---

### Post by The Cog on 2010-09-07
Not without installing openrobots. 

Did it install to /usr/local/openrobots or did it install somewhere else instead? 

What's the name of the executable to launch it? I guessed at openrobots.

---

### Post by farouk2506 on 2010-09-07
HI again,,,,
yes openrobots is already there ,i mean the directory /usr/local/openrobots but there is nothing in the file openrobots!!
if it doesn't bother you , may i contact you directly by instant messages through an email account, and i guess we better try to disinstall and reinstall it again?

---

