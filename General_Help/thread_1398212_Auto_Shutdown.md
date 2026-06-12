---
title: "Auto Shutdown"
date: 2010-02-04
forum: General Help
---

### Post by A.A on 2010-02-04
How to Schedule auto shutdown in Ubuntu?
I am a newbie. Last night I have some downloads in progress while at the same time I really wanted to go asleep. So I wondered if there's a way to schedule auto shutdown the system after a set period of time. I heared its possible using command line but dont know the usage. 
 
Thanx in Anticipation!

---

### Post by Ordes on 2010-02-04
sudo shutdown -P time

if time
= number; > indicates minutes
e.g shutdown -P 40  >shutdown in 40 min

= xx:yy > indicates time  (24:00 hrs)
e.g shutdown -P 13:15  > shutdown at 13:15 


read more at 
man shutdown

---

### Post by 3rdalbum on 2010-02-04
Yep, it's very possible on the command-line, using that "at" command. You first run the 'at' command and tell it how long to wait, and then it brings up its own little command-line where you type the commands you want it to run at that time. Then you press Control-D to exit.

So first, you start 'at' and tell it what time to use:

```
sudo at now + 50 minutes
```

Or:

```
sudo at 10pm
```

Then type:

```
halt
```

Then press Control-D.

If you decide you want to cancel the shutdown (especially if you're going to shut down manually earlier), then you can use the "sudo atq" command to check the ID numbers of the pending tasks, and then the "sudo atrm <id>" command to remove the task.

EDIT: Ordes' solution is "better" when you're talking about just shutting down the system, but you should learn how to use 'at' anyway as it might come in handy!

Also, the program "gnome-schedule" is a GUI for scheduling tasks, including shutdowns.

---

### Post by kantu on 2010-02-04
isnt it shutdown -P +45
i am not sure correct me if wrong

---

### Post by Ordes on 2010-02-04
shutdown -P +45
shutdown -P 45

they both seem to work; in the man they actually say +45; never recognized it as i always just used the number without the +...

---

### Post by konqueror7 on 2010-02-04
or if you want a graphical interface, try installing [GShutdown]("apt://gshutdown"),
```
sudo apt-get install gshutdown
```

---

### Post by A.A on 2010-02-04
Thanks for your help Buddies.
Linux really makes things easier...

---

### Post by hemimaniac on 2010-02-04
> **konqueror7 said:**
> or if you want a graphical interface, try installing [GShutdown]("apt://gshutdown"),
```
sudo apt-get install gshutdown
```

Neat, been using *unix for over a year and I didn't know about that one, I usually pop open a terminal and do;

screen -S shutdown
sudo shutdown -[rh] ti:me
ctrl+a d

Thanks

---

### Post by funkelauge on 2010-02-04
If you want to run shutdown without user privileges use
```
sudo chmod a+x /usr/bin/shutdown
```

This way all users&programs can issue the command.

Cheers,

funkelauge

---

### Post by hemimaniac on 2010-02-04
> **funkelauge said:**
> If you want to run shutdown without user privileges use
```
sudo chmod a+x /usr/bin/shutdown
```This way all users&programs can issue the command.

Cheers,

funkelauge

I get no such file when I try that, but 

sudo chmod u+s /sbin/shutdown

works for me

??

---

### Post by FahadMKS on 2010-09-25
> **Ordes said:**
> sudo shutdown -P time

if time
= number; > indicates minutes
e.g shutdown -P 40  >shutdown in 40 min

= xx:yy > indicates time  (24:00 hrs)
e.g shutdown -P 13:15  > shutdown at 13:15 


read more at 
man shutdown

Hey, this is good and it really works.
The only issue is that we need to be Root so as to get the issue resolved.

---

### Post by katya_sehgal on 2011-12-08
> **FahadMKS said:**
> Hey, this is good and it really works.
The only issue is that we need to be Root so as to get the issue resolved.

This looks good. Is there a similar script for hibernation?

---

### Post by oldos2er on 2011-12-08
Closed, please start a new thread for your question.

---

