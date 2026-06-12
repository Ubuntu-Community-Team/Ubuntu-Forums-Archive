---
title: "process in bg = no more use of shell session ?"
date: 2011-04-05
forum: General Help
---

### Post by tzoma on 2011-04-05
Hello,

First of all - still new to ubuntu :(
I ran into a dead-end today . I opened a terminal window, started pidgin, and logged on to ymsg. 
I've chatted for a while, but seeing how my buddy went to grab a bite to eat, i went back to the console to install acrobat reader. I saw that pidgin was still running, so I CTRL+Z to put it into the background. 

However, it stopped my pidgin session. I knew that this key-comb was to switch between proceses ... so now i'm stuck. What am i doing wrong ? 

Isn't there any possibility to be able to work in CLI and still have a pidgin (or firefox, for that matter) session open and running ? 

Thank you

---

### Post by CharlesA on 2011-04-05
Run it with a "&"

```
pidgin &
```

Either that or just open another terminal (or just run pidgin from the panel)

---

### Post by tzoma on 2011-04-05
Yep - this was it . 

Thanks a lot :)

---

### Post by WorMzy on 2011-04-05
Ctrl+Z suspends the process, "fg" recalls it. If you have multiple suspended processes, you can use the "jobs" command list them, then recall the specific job with "fg %[COLOR="Red"]#[/COLOR]" (replacing [COLOR="Red"]#[/COLOR] with the job number).

---

### Post by bodhi.zazen on 2011-04-05
There are several potential solutions to this issue.

One problem is that using the & , if you close the terminal, the application is also terminated.

You can use screen, dtach, and nohup.

```
nohup pidgin &
```

and then you will be able to close the terminal and pidgin will continue to run.

Screen and detach are better for ssh (you can re-connect to the sessions).

---

### Post by tzoma on 2011-04-06
You know, that was what I was about to ask - how to keep my processes open even when i close down the terminal :D

Thanks guys !

---

