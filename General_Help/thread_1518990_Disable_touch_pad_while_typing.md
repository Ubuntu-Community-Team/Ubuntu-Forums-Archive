---
title: "Disable touch pad while typing"
date: 2010-06-27
forum: General Help
---

### Post by _AltF4_ on 2010-06-27
Where is the "disable touch pad while typing" preference stored and how can I alter it without using the GUI?

I have written a script to disable my touch pad, but if the "disable touch pad while typing"  preference is on it the touch pad will reactivate its self after I type. Clearly the "disable touch pad while typing" preference must be stored somewhere, if someone could tell me where I could alter my script to disable the preference along with my touch pad. 
I hope I am making sense. 

My current script:
```
state=`synclient -l | fgrep TouchpadOff | sed 's/^.*= //'`
if [ $state -eq 1 ]
then
        synclient TouchpadOff=0
else
        synclient TouchpadOff=1
fi
exit 0
```



If this is not the right subforum please just tell me where to go.

---

### Post by _AltF4_ on 2010-06-27
bump

---

### Post by _AltF4_ on 2010-06-27
bump

---

### Post by KdotJ on 2010-06-27
Why do you want to write your own script? Why not use the existing one?

---

### Post by _AltF4_ on 2010-06-28
> **KdotJ said:**
> Why do you want to write your own script? Why not use the existing one?
What existing one? If you are talking about the basic disable touch pad while typing, I find it inadequate at times but would like to keep it enabled because of its inherent utility.

---

