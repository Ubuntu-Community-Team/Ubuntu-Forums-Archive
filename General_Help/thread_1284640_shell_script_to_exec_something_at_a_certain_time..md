---
title: "shell script to exec something at a certain time."
date: 2009-10-06
forum: General Help
---

### Post by TwinStinger on 2009-10-06
Hi there.

Still a bit of a noob, have read a little about crontab but I'm not certain it can do what i want.

So I figured I might be able to do it with a shell script.

This is what I want to accomplish:

Have 4 or five different scripts that starts "vlc mms://wm-live.sr.se/SR-Stockholm-High" at a certain time.

One script starts it at 07.00 another at 08.00 and so on...

I know I can use ie sleep 7h but I simply wants to klick and tell my vlc to start my radio station at 07.00 or 08.00.


I can make a script that starts the app with the adress but how to do it at a certain time? 

Belive that someone out there has the answer and I would be very happy 
for any idea on how to solve this.

/ Twinned

---

### Post by dcstar on 2009-10-06
> **TwinStinger said:**
> Hi there.

Still a bit of a noob, have read a little about crontab but I'm not certain it can do what i want.

So I figured I might be able to do it with a shell script.

This is what I want to accomplish:

Have 4 or five different scripts that starts "vlc mms://wm-live.sr.se/SR-Stockholm-High" at a certain time.

One script starts it at 07.00 another at 08.00 and so on...

I know I can use ie sleep 7h but I simply wants to klick and tell my vlc to start my radio station at 07.00 or 08.00.


I can make a script that starts the app with the adress but how to do it at a certain time? 

Belive that someone out there has the answer and I would be very happy 
for any idea on how to solve this.

/ Twinned

Install the **gnome-schedule** package: Applications-System Tools-Scheduled tasks.

---

### Post by TwinStinger on 2009-10-06
Thank you but I'm running openbox so I'm not sure if I would like to have a gnome app.

I really would like to do it with a script or crontab if possible.

The thing is that I would like to create a shortcut in my openbox menu 
that says "Wake up at 07.00" and then simply executes a script that starts vlc with my radio station at that time.

/ Twinned

---

### Post by blueridgedog on 2009-10-06
> **TwinStinger said:**
> 
Have 4 or five different scripts that starts "vlc mms://wm-live.sr.se/SR-Stockholm-High" at a certain time.


You can edit your crontab file with:

```
crontab -e
```

The format of the file is:

minute hour dayofmonth month dayofweek   command

So, to run it at 7 and 8, the single line would look like:

```
0 7,8 * * * vlc mms://wm-live.sr.se/SR-Stockholm-High
```

Meaning, at 7 and 8 AM on every day of the week and every day of the month run the command.

The editor is vi, which may need some explanation of its own if you are not familiar with it.

---

### Post by jonobr on 2009-10-06
+1 with blueridgedog

crontab is exactly what you need to accomplish this

---

### Post by TwinStinger on 2009-10-06
Thank you very much!

Spent a couple of hours reading on crontab and have also created a working one.

I have nano, have actually used Vi but it's a bit to hardcore for me :)

I think I will come up with a solution. The thing is that the cron-job is still around after being used and I don't know if I have to wake up at 7, 8 or 9 the day after.

So figured that I have to learn a bit more about crontab.

Maybe something like this might work?

A root crontab that does "crontab -e" on the users crontab at 10 every morning and then 3 different sh-scripts that creates a new crontab that starts vlc at 7,8 or 9.
 
What do you think?

/ Twinned

---

### Post by renkinjutsu on 2009-10-06
once you make a cron job.. that entry STAYS until you delete it ;)

you don't have to do anything as complicated as using ANOTHER cron job to add cronjobs to users (that's what you're saying right?)

---

### Post by diesch on 2009-10-06
If you want it to be run just once use at:

```

echo "vlc mms://wm-live.sr.se/SR-Stockholm-High" | at 7:00 tomorrow

```

---

### Post by TwinStinger on 2009-10-06
Yes, the problem is that it stays.

If have to wake up at 7 on Monday but on Tuesday I can sleep untill 9 then it would be sad to be woken up at 7.

Maybe the best thing would be to have sh-script to first run crontab -r
and then create a new with the desired time?

On the other hand  if it's an Saturday I might wanna sleep until I wake up without being disturbed by my scheduled vlc-radio. Then I manually have to run crontab -r.

/ Twinned

---

### Post by TwinStinger on 2009-10-06
> **diesch said:**
> If you want it to be run just once use at:

```

echo "vlc mms://wm-live.sr.se/SR-Stockholm-High" | at 7:00 tomorrow

```



AHHHHH!!!    Thank you diesch
   
That sounds great, a super simple solution.
I will try it out tomorrow.

will echo "vlc mms://wm-live.sr.se/SR-Stockholm-High" | at 7:00 today
work as well?

Thanks 

/ Twinned

---

### Post by TwinStinger on 2009-10-06
Hmm got this message when I tried it out:


twinned@twinned-laptop:~$ echo "vlc mms://wm-live.sr.se/SR-Stockholm-High" | at 7:00 tomorrow
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: No such file or directory


:(

---

### Post by renkinjutsu on 2009-10-06
yeah, that'll work (the today isn't necessary though)


also, one thing to remember about "at" or "cron" is that they use a 24 hour clock D; silly mistakes can cost you

---

### Post by diesch on 2009-10-06
at understands a lot of time  specifications, see [ the manpage for at]("http://manpages.ubuntu.com/manpages/jaunty/en/man1/at.1.html") for some examples.

---

### Post by Vrekk on 2009-10-06
the 
```
echo "COMMAND" | at 7:00 today
```
will run if it it before 7:00AM.  Make sure you use either am/pm or tell it the time in a 24 clock.

If you were to tyep
```
echo "COMMAND" | at 7:00
```
The code will run the next time it is 7AM and that could be tomarrow

---

### Post by TwinStinger on 2009-10-06
Seems to be some ownership problem and missing of a file.

Found what I think is the solution to the problem.

Thank you all very much.

I'll be back with a report tomorrow night.



where i found the (hopefully) solution:

[http://lucky13linux.wordpress.com/category/get-productive/](http://lucky13linux.wordpress.com/category/get-productive/)

won't trust the solution today since I have to wake up in 5 hours....  :)



/ Twinned

---

### Post by blueridgedog on 2009-10-07
You need to understand the tool, not the solution suggested.

If you want it to work on Monday and Tuesday only, at 7 and 8 am, then:

```
0 7,8 * * 1,2 vlc mms://wm-live.sr.se/SR-Stockholm-High
```

If you wanted it at 9 on Wednesday and at 7 Monday and Tuesday:

```
0 7 * * 1,2 vlc mms://wm-live.sr.se/SR-Stockholm-High
0 9 * * 3 vlc mms://wm-live.sr.se/SR-Stockholm-High
```

The last section is "day of week" with Sunday being 0, so 1 is Monday and 2 is Tuesday and so on.

You can have it any way you like it with crontab, it is the most flexible "set it and forget it" tool for managing tasks that occur at intervals that you will ever find.

Once you set these commands, they will run until you remove them.

---

### Post by TwinStinger on 2009-10-07
Thank you blueridgedog.

But I don't want it to be on a reoccurring basis.

Think of it like this:

One night coming home from work I got an assignment and need to be at a customer at 11 o'clock the following morning.
I didn't know which time until that very evening.

So I want it to work like a alarm clock with 5 or more preset wake up times.

Of course I can do a new crontab before I go to sleep but that feels unnecessary since "at" does exactly the thing I want.


Here is my solution:

I have a bunch of simple scripts looking like this, with different times.
--------------------------------------------------------------------------
#!/bin/bash

echo "vlc mms://wm-live.sr.se/SR-Stockholm-High" | at 07:00
--------------------------------------------------------------------------

Then I made entries in my openbox menu.xml using the GUI obmenu.

**Label** 07.00 

**Execute** /home/twinned/.scripts/wake0700.sh



It works great and it looks nice :D  

[[IMG]http://img28.imageshack.us/img28/5297/screen0710.th.jpg[/IMG]](http://img28.imageshack.us/i/screen0710.jpg/)




Thank you for helping me out.

/ Twinned

---

### Post by blueridgedog on 2009-10-07
I see...you want to be able to tweak it from nigh to night.  It appears you have the right tool for your impromptu alarm clock.

---

### Post by stefanadelbert on 2009-10-12
It's possible to set an alarm in Evolution Calendars and have the alarm run a program with parameters (your vlc command). You could associate the alarm with an event that repeats every day and then just drag the individual calendar events to different time slots as required. Evolution integrates with the time applet on the Gnome panel too. Could be a nice solution, although you do seem happy with the one you already have!

---

