---
title: "Ping, CPU, Memory - Coding Help"
date: 2011-08-03
forum: General Help
---

### Post by Joseph889 on 2011-08-03
Hello,

I am writing a script that will ping a server and then do a command if it gets a ping that is less than 100ms or more than 100ms. Basically, I need to have a variable for the ms. Here is an example script.

```
ping -c 1 25.25.25.25
if [ $pingms -gt 100 ]
then
sendemail (arguments here)
else
echo Ping good!
fi
```

Now, all I need to do is get a variable from the ping. I know I can do this:

```
pingms=`ping -c 25.25.25.25 | grep 'time='`
```

But that just sets the whole line, I only want the ping, without "ms" at the end.

So basically, if I ping 25.25.25.25 and get 43.872 ms I want $pingms to equal 43.872. Any help is appreciated!

Also, how can I do this with free, for example:

```
free -g
```

I want $ramavail to equal the amount available and I want $ramtotal to equal the total amount. Thanks!!

---

### Post by Beacon11 on 2011-08-03
For the ping, try something along the lines of:

```
pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
```

Note that this is unit-agnostic, as you requested. What if it isn't in milliseconds?

For the memory, try something like:

```
ramavail=`free -g | awk '/Mem:/ {print $4}'`
ramtotal=`free -g | awk '/Mem:/ {print $2}'`
```

Personally, I find free -m to be more helpful, and the above code will still work.

For more information, check out the man pages for sed and awk, and also check out [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html) for sed and [http://www.gnu.org/software/gawk/manual/gawk.html](http://www.gnu.org/software/gawk/manual/gawk.html) for awk.

---

### Post by Joseph889 on 2011-08-03
> **Beacon11 said:**
> For the ping, try something along the lines of:

```
pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
```Note that this is unit-agnostic, as you requested. What if it isn't in milliseconds?

For the memory, try something like:

```
ramavail=`free -g | awk '/Mem:/ {print $4}'`
ramtotal=`free -g | awk '/Mem:/ {print $2}'`
```Personally, I find free -m to be more helpful, and the above code will still work.

For more information, check out the man pages for sed and awk, and also check out [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html) for sed and [http://www.gnu.org/software/gawk/manual/gawk.html](http://www.gnu.org/software/gawk/manual/gawk.html) for awk.

That works, thanks!

But I have another problem, here is the code:

```
#!/bin/sh
while true; do
pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
echo Your ping is: $pingms
if [ $pingms -ge "99" ]
then
sendemail (arguments hidden for privacy)
fi
sleep 3
done

```

And what I run it I get:

```

Your ping is: 39.0
[: 10: Illegal number: 39.0
```

Any ideas how to fix this?

---

### Post by Joseph889 on 2011-08-03
Wait a second! Changed ```
#!/bin/sh
``` to ```
#!/bin/bash
``` and now when I run it I get: ```
/bin/testping.sh: line 5: [: 40.3: integer expression expected

```Sorry with bothering you so much about this, but the help is much appreciated.

EDIT: Got it working fine. Thanks for your help.

---

### Post by Beacon11 on 2011-08-04
> **Joseph889 said:**
> EDIT: Got it working fine. Thanks for your help.

Hey no problem, sorry, you were posting while I was asleep ;) . Let me know if you have any more questions!

---

### Post by Joseph889 on 2011-08-04
> **Beacon11 said:**
> Hey no problem, sorry, you were posting while I was asleep ;) . Let me know if you have any more questions!

If you could help me with [this (click here)]("http://ubuntuforums.org/showthread.php?p=11119084") it would be great.

---

