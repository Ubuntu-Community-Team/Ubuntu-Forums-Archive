---
title: "start just X at bootup?"
date: 2009-12-02
forum: General Help
---

### Post by Xbehave on 2009-12-02
How can i start just X at the end of my bootup?
I've tried putting the following line in my rc.local and in a custom upstart script
```
su juan -c "bash --login -c startx" 
```
But it seams to fail, and i'm not sure why? (it works fine when run from a root login)

I know this is a bit weird as i could just use *dm but, I've put to gether a very minimal install that boots very quickly and i'd rather not add more than i need to.

---

### Post by Xbehave on 2009-12-03
OK so i played around abit and i can get a root xorg running by launching the following script (from rc.local to keep it simple)

/etc/startmyx.sh```
#!/bin/bash
declare -x HOME="/root"
declare -x HUSHLOGIN="FALSE"
declare -x LANG="en_GB.UTF-8"
declare -x LOGNAME="root"
declare -x MAIL="/var/mail/root"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x SHLVL="1"
declare -x USER="root"

cd $HOME
startx
su juan -c /usr/bin/startx
su juan -| -c "/bin/bash --login -c /usr/bin/startx"
```However the last 2 lines fail "silently"(nothing goes to the kerminal and nothing  in xorg.0.log stands out to me)

/etc/startjuan.sh```
#!/bin/bash
declare -x HOME="/home/juan"
declare -x HUSHLOGIN="FALSE"
declare -x LANG="en_GB.UTF-8"
declare -x LOGNAME="juan"
declare -x MAIL="/var/mail/juan"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x SHLVL="1"
declare -x USER="juan"

cd $HOME
startx
```This fails, even when called by /etc/launchsu.sh
```
#!/bin/bash
su juan -c "/etc/startjuan.sh"
```meaning the total failure of an rc.local looks like```
/etc/rc.local
/etc/startmyx.sh
/etc/launchsu.sh
su juan -c "/etc/startjuan.sh"
```well the 1st line works

---

### Post by NoaHall on 2009-12-05
Try adding this to your bash_profile -
```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
  startx
  logout
fi
```

---

### Post by Xbehave on 2009-12-05
I have something similar at the moment but i'd like autologin.

---

### Post by NoaHall on 2009-12-05
Can you post the output of ```
 cat /etc/inittab 
``` so I can see what it looks like right now?

---

### Post by Xbehave on 2009-12-05
I don't have one, I think ubuntu uses upstart to do all that jazz so i once i get a way of launching X as me from a startup script, i'll play with upstart but the problem is i cant get X launched (i've played with startx mainly but even raw X doesn't do well)

---

### Post by markthecarp on 2009-12-05
Hey Xbehave,

This may not be exactly what you are trying to do but try editing /etc/init/gdm.conf, line 12 or 13 (varies between karmic and lucid), to read
```

stop on runlevel [0126]

```
rather than the default
```

stop on runlevel [016]

```

This will prevent gdm from starting. You will be presented with a console login. Login and enter
```

startx

```
You can customize what DE or window manager starts by making a custom ~/.xinitrc file. Obviously this assumes you have gdm installed. Hum, reading your OP I may be way off base from what you're trying to do.

A commenter on a blog post of mine offered some other options.

[upstart-trickery]("http://www.markthecarp.net/2009/11/upstart-trickery.html")

-mark

Edit: re-reading your original post I don't think auto login is possible w/o using a display manager.

---

### Post by NoaHall on 2009-12-05
Well, here's this -
/bin/su juan R -l -c "/bin/bash --login -c /usr/bin/startx >/dev/null 2>&1"
Try putting that in and see.
That's what I've used in the past.

---

### Post by Xbehave on 2009-12-05
> **NoaHall said:**
> Well, here's this -
/bin/su juan R -l -c "/bin/bash --login -c /usr/bin/startx >/dev/null 2>&1"
Try putting that in and see.
That's what I've used in the past.
I've been trying pretty much that but i modified it to give me an error log and now know the cause of the problem
```
X: user not authorized to run the X server, aborting.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```
I'm not authorised to run the X, i guess its to do with su and setuid :S but i've got somewhere to start looking now :D

**Solved**
Following on from that i just had to run 
```
sudo dpkg-reconfigure x11-common
```
to allow anybody (from [here]("http://ubuntuforums.org/showthread.php?t=255148"))

---

