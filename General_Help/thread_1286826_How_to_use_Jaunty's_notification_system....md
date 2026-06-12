---
title: "How to use Jaunty's notification system..."
date: 2009-10-09
forum: General Help
---

### Post by x C0MMAND0 x on 2009-10-09
I have googled and searched for this but I have not been able to find any answers.  Long story short, I have a script that generates random jokes.  I would like to know how to output data into Jaunty's notification area.  Then, I will set the task to run scheduled as a cron job.  

My goal here is to have a random joke pop up as a notification every hour or so.

Is there a way/app/script to make use of Jaunty's excellent notification system?

---

### Post by sisco311 on 2009-10-09
```
notify-send "random joke" "don't drink unwashed fruite juice" 
```

---

### Post by x C0MMAND0 x on 2009-10-09
I just tried that code you posted.

```
brent@Prometheus:~$ sudo apt-get install notify-send
[sudo] password for brent: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package notify-send

```

How do I get "notify-send"?  What is the necessary repository?

---

### Post by sisco311 on 2009-10-09
it in the libnotify-bin package in the universe repos (probably enabled):
```
sudo apt-get install libnotify-bin
```

---

### Post by x C0MMAND0 x on 2009-10-09
It's still not letting me install after running that...

---

### Post by x C0MMAND0 x on 2009-10-09
Nevermind, it is!  Thank you!!!

---

