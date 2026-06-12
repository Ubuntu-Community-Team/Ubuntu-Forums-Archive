---
title: "Always run another command after ant"
date: 2010-01-20
forum: General Help
---

### Post by richiethom on 2010-01-20
Hi

I use ant all the time, and would like to be able to automatically run notify-send after ant has finished, like this:

[FONT="Courier New"]ant big series of long targets ; notify-send "Ant complete"[/FONT]

Is there a way that I can accomplish this? I'm running Ubuntu 9.10 and the ant installed is from the repository.

Thanks in advance

Rich

---

### Post by nigel_nb on 2010-01-20
I'm not sure how its done and the documentation for notify-osd is not much, but feel free to take a look at [https://wiki.ubuntu.com/NotificationDevelopmentGuidelines](https://wiki.ubuntu.com/NotificationDevelopmentGuidelines) and create a script.

---

### Post by richiethom on 2010-01-20
Thanks. The problem I have is how to create that script. I know nothing about scripting, nor about how to make sure that when I type

ant target

it correctly runs:

ant target ; notify-send "Ant finished"

(and doesn't enter an endless loop, for example, with the script calling itself)

Rich

---

### Post by KeLa on 2010-01-20
For example create new empty file to your home directory let's say rant
and open it in editor and write to it following:
```

ant target && notify-send "Ant finished"
```
then run following in your home dir
```
chmod 755 rant
```
and after that you just run rant and it will do the job.

---

