---
title: "tty changes?"
date: 2010-11-09
forum: General Help
---

### Post by COKEDUDE on 2010-11-09
I am not sure if I am using the correct terminology but somehow my tty keeps changing on me. The man pages are confusing to me on what exactly the tty is. This is what I see when I run the tty command. Could anyone explain why my tty keeps changing? 

```
~ $ tty
/dev/pts/1
```

```
~ $ tty
/dev/pts/0
```

---

### Post by Cheesehead on 2010-11-09
You are probably entering 'tty' on two different terminal windows.
Each treminal window mounts on a different tty. You're looking under the hood at how the system tells them apart.

try 'man tty' for more information.

---

### Post by efflandt on 2010-11-09
Just to show you an example, in this case I logged into a text console (Ctrl+Alt+F2) which is tty2, X runs in tty7 (Alt+F7 takes me from console back to X), and pts/0 is an X terminal that I copied that from.  If you open more than one terminal, each will have a different pts/#.  By default there are 6 tty consoles (F1-F6) plus X on tty7 (F7).  Alt+F# takes you from console to console, but to get to console from X you have to use Ctrl+Alt+F#.

efflandt@XPS-8100:~$ who
efflandt tty2         2010-11-09 22:42
efflandt tty7         2010-11-07 08:01 (:0)
efflandt pts/0        2010-11-09 22:41 (:0.0)

---

### Post by COKEDUDE on 2010-11-10
Could you tell me how to write a shellscript that checks what tty you are using and then uses that tty? I have a few shellscripts that depend on me picking the write tty.

---

### Post by COKEDUDE on 2010-11-18
Could anyone help me with this?

---

### Post by efflandt on 2010-11-18
```
#!/bin/sh
mytty=`tty` #note: backticks (grave) not single quotes
echo $mytty
```Note that **/bin/sh** uses **dash** instead of bash.  So if your script uses anything **bash** specific, the first line should be **#!/bin/bash**

---

### Post by COKEDUDE on 2010-11-18
> **efflandt said:**
> ```
#!/bin/sh
mytty=`tty` #note: backticks (grave) not single quotes
echo $mytty
```Note that **/bin/sh** uses **dash** instead of bash.  So if your script uses anything **bash** specific, the first line should be **#!/bin/bash**

Thank you very much for explaining that so well. I definitely would not have noticed that I needed to change **#!/bin/sh** to **#!/bin/bash**. 

Could you explain how to type backticks on your keyboard? I couldn't figure out how to do it. 

If your curious here is my shellscript that I added this to. 

```
#!/bin/bash
mytty=`tty` #note: backticks (grave) not single quotes
echo $mytty
set -x
/usr/bin/xhost +localhost
DISPLAY=:0.0
export DISPLAY
LANG=en_US.utf8
export LANG
/usr/bin/vlc -L "/home/bob/Desktop/The Patriot/The Patriot.avi" <$mytty >$mytty 2>&1
exit 0

```

---

### Post by efflandt on 2010-11-19
Back tick or grave (`) is usually in upper left of US keyboard, basically an unshifted tilde (~).  Although, on laptops it may be juggled around somewhere else.

Backticks around something execute that command in the shell and return its output, in this case assigned to the variable mytty.  There may be other characters you could wrap around a command to execute it and grab its output, but backticks are a common method used within Perl scripts too.

---

### Post by COKEDUDE on 2010-11-22
> **efflandt said:**
> Back tick or grave (`) is usually in upper left of US keyboard, basically an unshifted tilde (~).  Although, on laptops it may be juggled around somewhere else.

Backticks around something execute that command in the shell and return its output, in this case assigned to the variable mytty.  There may be other characters you could wrap around a command to execute it and grab its output, but backticks are a common method used within Perl scripts too.

Wow thats funny. I use the tilde all the time. It just looks like a backwards comma on the keyboard to me. On my laptop it is in the top left corner. Thank you for all of the help.

---

