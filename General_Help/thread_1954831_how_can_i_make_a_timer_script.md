---
title: "how can i make a timer script?"
date: 2012-04-08
forum: General Help
---

### Post by chestycuogth on 2012-04-08
ok. i like to eat cheese toasty's - all the time. unfortunately i dont have a egg timer and i tend to lose track of time when i'm on the computer, so my cheese toasty's often get burnt.


QUESTION: i would like to know how to make a bash script that sets off a timer when the script is run. and then opens a given file (like a text document that says "check your cheese toasty!") when the timer runs out. i know how to open files and start applications through the terminal, but i dont know how to set the launch on a timer.

PS. i dont want to sound like an ungrateful, picky bastard, but dont link me to applications that can do this for me - if i learn how to make a script that can do this then it could be quite versatile.
thanks.

---

### Post by ridetheteapot on 2012-04-08
the sleep command will do it just fine.
check man sleep, it will take minutes, hours, and default seconds.

sleep $1; notify-send "Hey check the toaster buddy!"; ogg123 SCREAM.ogg

would be pretty basic but would work fine.

EDIT___
hey just curious, what country are you from where they are called cheese toasties? I am thinking of what i call a grilled cheese - dela usa

---

### Post by chestycuogth on 2012-04-08
> **ridetheteapot said:**
> 
EDIT___
hey just curious, what country are you from where they are called cheese toasties? I am thinking of what i call a grilled cheese - dela usa

i'm from the uk.
i'm talking about a cheese sandwich that you put under the grill to make  a toasted sandwich

---

### Post by ridetheteapot on 2012-04-08
yea grilled cheese over here xD ima switch it up, i like the way cheese toastie sounds

---

