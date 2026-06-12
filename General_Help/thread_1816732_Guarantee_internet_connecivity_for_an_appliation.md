---
title: "Guarantee internet connecivity for an appliation"
date: 2011-08-02
forum: General Help
---

### Post by Kissell on 2011-08-02
I have an application that runs through an automated script and it is extremely vital that it have internet connectivity when it runs. 

However, bandwidth usage is often maxed out by an offsite backup program.

The backup program runs on the same ubuntu box.

Is there a way to guarantee my script's application can get internet connectivity when it runs?  

Ideally I would like some sort of TCP quality of service solution, I never want to limit the backup programs speed, except while my script is running.  I also, ideally, i never want to stop or kill the backup from running, i'm worried that it would corrupt the current file being transferred.

Can I suspend or pause an already running process of the backup and then resume it at the end of my script?  I have the ability to run the script as root.

---

### Post by blind2314 on 2011-08-02
> **Kissell said:**
> I have an application that runs through an automated script and it is extremely vital that it have internet connectivity when it runs. 
 
However, bandwidth usage is often maxed out by an offsite backup program.
 
The backup program runs on the same ubuntu box.
 
Is there a way to guarantee my script's application can get internet connectivity when it runs? 
 
Ideally I would like some sort of TCP quality of service solution, I never want to limit the backup programs speed, except while my script is running. I also, ideally, i never want to stop or kill the backup from running, i'm worried that it would corrupt the current file being transferred.
 
Can I suspend or pause an already running process of the backup and then resume it at the end of my script? I have the ability to run the script as root.
 
 
If you know the PID of the backup program, you can send a SIGSTOP and SIGCONT to pause and resume it, respectively.
 
```
kill -stop $pid
kill -cont $pid
```

---

### Post by Kissell on 2011-08-02
> **blind2314 said:**
> If you know the PID of the backup program, you can send a SIGSTOP and SIGCONT to pause and resumse it, respectively.
 
```
kill -stop $pid
kill -cont $pid
```

Thanks, that works great.  It never occurred to me that the kill command could do that, since you know, the name is a little threatening.

But, if I reboot the server the pid is probably going to be different...  :(

---

### Post by blind2314 on 2011-08-02
> **Kissell said:**
> Thanks, that works great. It never occurred to me that the kill command could do that, since you know, the name is a little threatening.
 
But, if I reboot the server the pid is probably going to be different... :(
 
Yes, it most certainly will be different. If the process always runs under a reliable name though, getting the PID in your script is trivial.
 
```
pid=`ps -ef | grep <process name> | grep -v grep | awk '{print $2}'`
kill -stop $pid
kill -cont $pid
```

---

### Post by Kissell on 2011-08-02
When I echo/tested the command to get the PID I got two numbers.
> 
5469 9373


So I tested the code, and "ps" is returning two results, one is the result I want, and a second result is my search for the result I want.

ps -ef|grep gnome-terminal
> 
user1     5469     1     0 Aug01 ?     00:00:41 gnome-terminal
admin1    9373  9303     0 10:56 pts/0 00:00:00 grep --colorauto gnome-terminal


It seems the "awk print $2" part is giving me the entire second column, not the second word.

---

### Post by blind2314 on 2011-08-02
> **Kissell said:**
> When I echo/tested the command to get the PID I got two numbers.
 
 
So I tested the code, and "ps" is returning two results, one is the result I want, and a second result is my search for the result I want.
 
ps -ef|grep gnome-terminal
 
 
It seems the "awk print $2" part is giving me the entire second column, not the second word.
 
See my edit above. I added ```
grep -v grep
``` to take away the process that is you searching for the PID itself.
 
Also, awk is functioning exactly how it should, it's simply giving you the second "word" of each result. Since you have 2, you're getting 2 results, or in effect the 2nd column.

---

### Post by Kissell on 2011-08-02
```
pid=`ps -ef | grep <process name> | grep -v grep | awk '{print $2}'`
kill -stop $pid
kill -cont $pid
```[/QUOTE]

Now that works perfect!  

I'm not comfortable with awk, but it is incredibly useful. 

That invert match (-v) is pretty cool too...  give me everything but the thing I'm asking for.  I've never seen that used before.  I suspect that'll be useful again someday.

Thanks so much!

---

