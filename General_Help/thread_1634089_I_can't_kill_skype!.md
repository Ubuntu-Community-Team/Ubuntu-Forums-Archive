---
title: "I can't kill skype!"
date: 2010-11-30
forum: General Help
---

### Post by lethalfang on 2010-11-30
This doesn't happen all the time, but right now I can't kill skype!
I noticed that it's consuming 100% of CPU, so I closed it on desktop, but it's still there consuming 100% of CPU. 
So I tried to send the kill signal "killall skype," and nothing happens.
Then, I tried to get the process ID "pgrep skype" and then "kill process_id," but skype is still consuming 100% CPU.
What the hell?

---

### Post by Rodney9 on 2010-11-30
You could try xkill, type ```
xkill
``` in terminal than click on skype.
Another thought, is it showing on the panel, can you right click on it's icon an select quit from there ?

---

### Post by lethalfang on 2010-11-30
> **Rodney9 said:**
> You could try xkill, type ```
xkill
``` in terminal than click on skype.
Another thought, is it showing on the panel, can you right click on it's icon an select quit from there ?

When I right-click to close Skype, it appears to quit, except the process was still running 100% CPU according to "top." And if I try to open Skype again, it will say that another instance of skype is running. 
It was the strangest thing I've ever seen on Ubuntu.

---

### Post by WorMzy on 2010-11-30
Try ```
killall -9 skype
```

---

### Post by anthonylane13 on 2010-11-30
```
sudo apt-get remove --purge skype
```
;)

---

### Post by WorMzy on 2010-11-30
That would remove skype, not stop the process.

---

### Post by anthonylane13 on 2010-12-01
> **WorMzy said:**
> That would remove skype, not stop the process.

Yes I know - I was being cheeky, hence the wink. Although removing it and reinstalling a different version might yield results.

---

### Post by lethalfang on 2010-12-05
> **WorMzy said:**
> Try ```
killall -9 skype
```

As for my original question, I restarted the computer before I tried this.
But I had another process I couldn't kill (mencoder) today, until I used the "-9" flag. It probably would've worked for Skype as well. 
Now I know how to kill a process that refuses to die! :P

---

### Post by Brisbane on 2011-10-09
yes killall -9 skype worked for me,
had the same issue, could not end process skipe could not kill [process_id] and it was using 96% of one of my CPU's

---

### Post by no2498 on 2011-10-10
look in your startup programs un click skype from the auto startup
windows has its hand on skype now days
also sounds like a flash problem

---

### Post by debd on 2011-10-10
u can try using a bash script like

```
#!/bin/bash
ps -e|grep skype|cut -c 2-5|xargs kill -9
```

---

### Post by keitwirik on 2012-04-02
thanks!
```
killall -9 skype
```
worked great for me. it's been helpful with other applications that run out of control.

---

