---
title: "What's wrong with my script?"
date: 2010-05-08
forum: General Help
---

### Post by dphirschler on 2010-05-08
I made a script which is supposed to end process for XBMC and/or MythTV.  The XBMC one works, but not the MythTV one.  When I run the script I get this message.

"Stopping processes:
/usr/local/bin/stop_all.sh: 29: Syntax error: "else" unexpected (expecting "then")"

Here is my script.

```

#!/bin/sh
echo "Stopping processes:"

#XBMC
# Test to see if it is running first
if pidof -s /usr/share/xbmc/xbmc.bin ; then
   # Try a clean kill
   ps aux|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill
   # takes a second or two to die with the soft kill
   sleep 2
   if pidof -s /usr/share/xbmc/xbmc.bin ; then
      ps aux|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill -9
      echo "XBMC stopped."
   else 
      echo "XBMC stopped (clean kill)."
   fi
else
   echo "XBMC not running."
fi

#MythTV
if [ `ps -C mythfrontend | grep -v PID` ]; then

   #kill the process
   kill -9 `ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'`
   sleep 2
   if [ `ps -C mythfrontend | grep -v PID` == "" ]; then

      echo "MythTV stopped."
   fi
else
   echo "MythTV not running."
fi

```

It's driving me crazy.  What am I missing here?


Darryl

---

### Post by Johnny B on 2010-05-08
does this line return more than one PID?
```
ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'
```

i would change it to:
```
for line in `ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'` ;do kill -9 $line ;done
```

---

### Post by iponeverything on 2010-05-08
> **Johnny B said:**
> does this line return more than one PID?
```
ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'
```

i would change it to:
```
for line in `ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'` ;do kill -9 $line ;done
```

or it could be shortened to:

```
pkill -9 mythfrontend.re
```

---

### Post by quadproc on 2010-05-08
I was trying to highlight part of  the script but the editor wouldn't let me so please ignore this post.

quadproc

---

### Post by dphirschler on 2010-05-08
> **Johnny B said:**
> does this line return more than one PID?
```
ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'
```

i would change it to:
```
for line in `ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'` ;do kill -9 $line ;done
```

I still get the same error with this statement.  There's got to be something wrong with my 'if' statements.


Darryl

---

### Post by Seal Daemon on 2010-05-08
Runs just fine on my PC .. :roll:

---

### Post by dphirschler on 2010-05-09
???

---

