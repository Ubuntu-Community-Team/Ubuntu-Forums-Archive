---
title: "How to change the amount of time before being logged out"
date: 2011-08-27
forum: General Help
---

### Post by Scottty on 2011-08-27
Hello 

My Computer logs me off all the time. I don't know how long but if feel like If I leave the computer alone for 5 minutes I have to login again.

I tried going to Control Center--> System--> and Login Screen and tried changing to logging in automatically but this didn't solve anything.

Can you suggest how to change the amount of time before I'm asked to login again.

Thank-you
Scott

---

### Post by AlphaLexman on 2011-08-27
Maybe the timeout variable is set.
```
echo $TMOUT
```
If it is not null or zero...
```
TMOUT=""
```

---

### Post by raja.genupula on 2011-08-27
are you doing log-in or unlock the screen after five min . i think you're doing unlock the screen . go to system settings -> screensaver preferences -->  uncheck the box of "lock the screen when screensaver active "

---

### Post by Scottty on 2011-08-27
raja.genupula

> are you doing log-in or unlock the screen after five min . i think you're doing unlock the screen . go to system settings -> screensaver preferences --> uncheck the box of "lock the screen when screensaver active " 

I went into Screensaver in the Personal section and I unchecked the 

Lock screen when screensaver is active.

Now it doesn't lock me out every 5 minutes.

Thank you

Scott

---

### Post by raja.genupula on 2011-08-27
aah that's great , please close the thread my marking it as solved in options thread tools  & remember this for everytime when you got solved with your issue .

---

