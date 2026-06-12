---
title: "Not Shutting Down Properly"
date: 2011-12-05
forum: General Help
---

### Post by tito-dutta on 2011-12-05
My computer (Ubuntu 11.04) is not shutting down properly. After clicking the shut down link it is staying long time in the Ubuntu screen (the general login/logout screen), finally I need to switch off the computer to shut it down.
What can I do?

---

### Post by flipper T on 2011-12-05
it is probably hanging on some process.
so, first thing to do is identify it.
goto a terminal, ctrl alt f1, and enter

```
sudo shutdown -r now

```then enter your password

this will try to reboot your computer
watch the messages and note which one is causing the delay.
report back when you know :)

i´m off to bed now, but will look in on this thread tomorrow.

---

### Post by tito-dutta on 2011-12-05
It is not working. Same problem. Taking long time in the purple color shut down window... finally no option remains other than switching off the computer from the switch board! :confused:

---

### Post by liferules on 2011-12-05
I have the same issue and have for quite some time ... back to 11.04. I agree it is probably a process that is handing... what is interesting is that:

sudo shutdown -r now 

shuts down properly....

---

### Post by tito-dutta on 2011-12-05
liferules,
Are you facing any problem in starting up of the computer? Is it starting up properly? 
(Hope you have subscribed this thread)

---

### Post by flipper T on 2011-12-06
just to clarify:

i had same problem in 11.04, now use 11.10 without issue.

you should be aware that

```
sudo shutdown -r now
```

should be run from the console(ctrl alt f1), and _**not**_ from the terminal (ctrl t).

for some reason it behaves differently in each.

so, try again.

---

