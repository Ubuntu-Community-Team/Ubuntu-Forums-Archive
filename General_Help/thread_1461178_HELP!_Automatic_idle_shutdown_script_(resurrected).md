---
title: "HELP! Automatic idle shutdown script (resurrected)"
date: 2010-04-23
forum: General Help
---

### Post by CyberCod on 2010-04-23
I found this script on [another forum post (HERE)]("http://ubuntuforums.org/showthread.php?t=530973") from a couple of years back... It doesn't work anymore for some reason and I'm looking for some assistance in making it work now.  I really need to cut down my electric bill and my son is constantly leaving his desktop on for hours on end.

Any gurus out there up to the challenge?

I am attempting to re-write the "inactive=...." line using *w* instead of *who*  but I'm not having much luck yet.

Any help out there?

```
#!/bin/bash
threshold=55
username=stream303
inactive=`who -a | grep $username | cut -c 45-46 | sort | grep [0-9] | head -n1 | sed 's/ //g'`

if [ "$inactive" != "" ]; then

echo "Idle time is: " $inactive

if [ "$inactive" -ge "$threshold" ]; then
echo "Threshold met so issuing shutdown command"
/sbin/shutdown -h now
else
echo "Below threshold"
fi
else
echo "Idle time is: 0"
fi
echo "Ending"
```


PS> I have changed the relevant portions of the script to line up with the system in question, so that isn't the problem.

---

### Post by CyberCod on 2010-04-24
bump

---

### Post by gsiliceo on 2010-08-23
Bump! in these days saving on energy is more important than ever, why doesnt ubuntu have this feature out of the box, and no, the sleep after ammount idle is not the solution, we want COMPLETE shutdown after ammount idle.

---

### Post by chang5562 on 2010-09-07
I had created an autoshutdown script using the same scheme - "who -a.." to catch the idle user.  However, my main application is a window application at the user session and I did not see any idle or non-idle time by user even the user did not use the window appl for a while. The time that "who -a" grabbed seems irrelevant to the idle time. So the script will run and shut down despite of active window. Anything wrong with "who -a".  I also tried with "w -s". the idle time of this actually started from the time that user login the system.

---

