---
title: "ubuntu logout command line"
date: 2010-06-30
forum: General Help
---

### Post by COKEDUDE on 2010-06-30
Besides the command listed below are there any other useful logout commands, to log out of ubuntu? I was quite surprised that logout doesn't work. Logout tells you to use exit and exit only closes your terminal window. 
```
gnome-session-save --kill --silent
```

---

### Post by bodhi.zazen on 2010-06-30
```
exit
```

Are you wanting to log out of a bash session (terminal) or an X session ?

---

### Post by garvinrick4 on 2010-06-30
```
sudo shutdown -h now
``` (shutdown)
```
sudo shutdown -r now
```  (restart)

---

### Post by Serpher on 2010-06-30
That's because the terminal the GUI uses is actually running in the backround, and the terminal windows are 'fake' terminals if you want to call it that. Press 'Ctrl + Alt + F1' (All the way to F6) to use a real terminal, and 'Ctrl + Alt + F7' to return to your GUI. There 'logout' will work.

---

### Post by Chame_Wizard on 2010-06-30
```
sudo halt now -h 
```

---

### Post by COKEDUDE on 2010-06-30
> **bodhi.zazen said:**
> ```
exit
```

Are you wanting to log out of a bash session (terminal) or an X session ?

Whats a X session? 

> **Serpher said:**
> That's because the terminal the GUI uses is actually running in the backround, and the terminal windows are 'fake' terminals if you want to call it that. Press 'Ctrl + Alt + F1' (All the way to F6) to use a real terminal, and 'Ctrl + Alt + F7' to return to your GUI. There 'logout' will work.

Is there a way to to that terminal from a shell script and also log in with that shell script? I know whenever you press 'Ctrl + Alt + F1' it always asks you to log in.

---

### Post by bodhi.zazen on 2010-06-30
> **COKEDUDE said:**
> Whats a X session? 

X = the graphical interface, the desktop. X is the system that manages your video, keyboard, and mouse.

[http://www.x.org/wiki/](http://www.x.org/wiki/)

The desktop interface (gnome, KDE, xfce) are built on top of X.

[http://xwinman.org/](http://xwinman.org/)

> Is there a way to to that terminal from a shell script and also log in with that shell script? I know whenever you press 'Ctrl + Alt + F1' it always asks you to log in.

What are you wanting to do exactly ?

It is confusing as you are new and you are not using "standard terminology". When you hit ctrl-alt-F1 you are at a console. 

In a graphical session, when you open a terminal, you are in a X session.

The command line is called bash.

The module, if you will, that manages login is called pam

[http://en.wikipedia.org/wiki/Linux_PAM](http://en.wikipedia.org/wiki/Linux_PAM)

---

### Post by Noz3001 on 2010-06-30
How about

```
# service gdm restart
```

---

### Post by COKEDUDE on 2010-06-30
> **bodhi.zazen said:**
> X = the graphical interface, the desktop. X is the system that manages your video, keyboard, and mouse.

[http://www.x.org/wiki/](http://www.x.org/wiki/)

The desktop interface (gnome, KDE, xfce) are built on top of X.

[http://xwinman.org/](http://xwinman.org/)



**What are you wanting to do exactly ?**

It is confusing as you are new and you are not using "standard terminology". When you hit ctrl-alt-F1 you are at a console. 

In a graphical session, when you open a terminal, you are in a X session.

The command line is called bash.

The module, if you will, that manages login is called pam

[http://en.wikipedia.org/wiki/Linux_PAM](http://en.wikipedia.org/wiki/Linux_PAM)

I'm working on writing a shell script that logs out whenever I have a firefox process running during certain times of the day (1 am - 8 am). I'll put it in crontab when it runs properly unless someone knows of a different and better way to do this. Here it is so far. 

```
if ps ax | grep firefox-3.6.3
then 
echo hi
/usr/bin/gnome-session-save --kill --silent
exit 0 
fi
```

Its not working yet cause grep isn't filtering the way I need it to. This is what I get when firefox is running. 
```
ps ax | grep firefox-3.6.3
 1859 ?        S      0:00 /bin/sh /usr/lib/firefox-3.6.3/firefox
 1864 ?        S      0:00 /bin/sh /usr/lib/firefox-3.6.3/run-mozilla.sh /usr/lib/firefox-3.6.3/firefox-bin
 1868 ?        Sl     1:45 /usr/lib/firefox-3.6.3/firefox-bin
 3374 pts/0    S+     0:00 grep --colour=auto firefox-3.6.3

```
This is what I get when firefox is not running. 
```
ps ax | grep firefox-3.6.3
 3374 pts/0    S+     0:00 grep --colour=auto firefox-3.6.3
```

I need it to ignore the grep filtering process.

---

### Post by blur xc on 2010-06-30
how about:

```
 sudo reboot
```concise and to the point...

It's funny because just last week I was wondering how to do this.

BM

---

### Post by COKEDUDE on 2010-06-30
> **blur xc said:**
> how about:

```
 sudo reboot
```concise and to the point...

It's funny because just last week I was wondering how to do this.

BM

I wanna logout not reboot :P.

---

### Post by blur xc on 2010-06-30
> **COKEDUDE said:**
> I wanna logout not reboot :P.


I guess my reply was more directed at post #3's sudo shutdown -r now to reboot.  sudo reboot is a lot less typing.

BM

---

### Post by Serpher on 2010-07-01
```
if ps ax | grep 1859
then 
echo hi
/usr/bin/gnome-session-save --kill --silent
exit 0 
fi
```

Every process has a number.

---

### Post by nmaster on 2010-07-01
> **COKEDUDE said:**
> I need it to ignore the grep filtering process.

try this instead:
```

top -b -n 1 | grep firefox

```

use whatever process name is appropriate.

---

### Post by nmaster on 2010-07-01
> **Serpher said:**
> ```
if ps ax | grep 1859
then 
echo hi
/usr/bin/gnome-session-save --kill --silent
exit 0 
fi
```Every process has a number.

that doesn't avoid the issue that the OP is having.  grep still finds itself in the output of ps

---

### Post by Serpher on 2010-07-01
> **neal.m.master said:**
> that doesn't avoid the issue that the OP is having.  grep still finds itself in the output of ps

Im' not sure what youre trying to say. Wouldn't it just check if Firefoxs process is running by using it's process number?

---

### Post by nmaster on 2010-07-01
> **COKEDUDE said:**
> Besides the command listed below are there any other useful logout commands, to log out of ubuntu? I was quite surprised that logout doesn't work. Logout tells you to use exit and exit only closes your terminal window. 
```
gnome-session-save --kill --silent
```

you need to kill Xorg and then try the logout command.

---

### Post by Serpher on 2010-07-01
I was just assuming the rest of his code worked. If the script were executed as root in the if statment Id put

```
service gdm restart
```

TBH your kid or whomever is just going to install Chrome or something. Stop network manager instead cutting off the internet at 1 and beyond, and turn it on after 8.

---

### Post by CannibalZerg on 2010-07-01
> **COKEDUDE said:**
> This is what I get when firefox is not running. 
```
ps ax | grep firefox-3.6.3
 3374 pts/0    S+     0:00 grep --colour=auto firefox-3.6.3
```I need it to ignore the grep filtering process.
Try one of this:
```

ps ax | grep [f]irefox
pgrep firefox 

```

---

### Post by nmaster on 2010-07-01
> **Serpher said:**
> Im' not sure what youre trying to say. Wouldn't it just check if Firefoxs process is running by using it's process number?

no.  it will check for any process that uses that set of characters.  that would include grep.  just try it.

---

### Post by nmaster on 2010-07-01
> **CannibalZerg said:**
> Try one of this:
```

ps ax | grep [f]irefox
pgrep firefox 

```

good point.  pgrep is probably best/easiest.

---

### Post by COKEDUDE on 2010-07-07
> **neal.m.master said:**
> try this instead:
```

top -b -n 1 | grep firefox

```

use whatever process name is appropriate.

That did the trick :). 

> **CannibalZerg said:**
> Try one of this:
```

ps ax | grep [f]irefox
pgrep firefox 

```

Both of these also did the trick. Could you explain why the first one worked? I don't understand how putting the f in square brackets did the trick.

---

### Post by CannibalZerg on 2010-07-08
> **COKEDUDE said:**
>  Could you explain why the first one worked? I don't understand how putting the f in square brackets did the trick.
Square brackets is a regexp "range expression". Expression *[f-h]irefox* means "firefox OR girefox OR hirefox". Expression *[f]irefox* means "firefox"(and nothing else), so comannds "grep firefox" and "grep [f]irefox" does the same thing: "firefox" substring serching. The trick is that string "3374 pts/0    S+     0:00 grep --colour=auto [f]irefox" doesn't contain substring "firefox".
See *man grep* for details.

---

### Post by COKEDUDE on 2011-01-30
I am having some problems with my script. 

```
#!/bin/bash

if ps ax | grep [f]irefox
then 
echo hi
/usr/bin/gnome-session-save --kill --silent
exit 0 
fi
```

I realized that firefox sometimes leaves **defunct processes**. How do I also ignore defunct processes? 

```
~ $ ps -ef | grep [f]irefox
bob      19635 19179  0 22:10 ?        00:00:00 [firefox] <defunct>

```

---

### Post by JKyleOKC on 2011-01-30
Try this:```
ps ax | grep firefox | grep -v grep | grep -v defunct
```The -v option shows all lines NOT matching the pattern, so the triple pipe first gets all matches, then removes any lines containing "grep" followed by removing any that match "defunct."

You can carry this on to as many levels as you need; it just takes thinking like the machine...

---

### Post by COKEDUDE on 2011-01-31
> **JKyleOKC said:**
> Try this:```
ps ax | grep firefox | grep -v grep | grep -v defunct
```The -v option shows all lines NOT matching the pattern, so the triple pipe first gets all matches, then removes any lines containing "grep" followed by removing any that match "defunct."

You can carry this on to as many levels as you need; it just takes thinking like the machine...

Thank you :). I simplified it a little like this. 

```
ps ax | grep [f]irefox | grep -v defunct
```

Here is the full code. 

```
#!/bin/bash

if ps ax | grep [f]irefox | grep -v defunct
then 
echo hi
/usr/bin/gnome-session-save --kill --silent
exit 0 
fi
```

---

### Post by MikeConklin on 2011-11-03
> **COKEDUDE said:**
> Besides the command listed below are there any other useful logout commands, to log out of ubuntu? I was quite surprised that logout doesn't work. Logout tells you to use exit and exit only closes your terminal window. 
```
gnome-session-save --kill --silent
```


code: service gdm restart (Gnome)
code: service lightdm restart (Unity)

---

### Post by oldos2er on 2011-11-03
Closed, please don't bump old threads.

---

