---
title: "Conky - how to delay startup so it doesn't mask other applications?"
date: 2011-05-21
forum: General Help
---

### Post by jamesjenner on 2011-05-21
G'day all,

I've been playing and tweeking conky and have got it running quite nicely. I created a script and put a sleep in it at the start with && and then put the script in the startup programs so that it would startup automatically.

Now I have the exact same configuration on a lappy (MacBook 5,1) and it works perfectly, starts up automatically and behaves how I like it. 

On my PC however I've been increasing the delay from 2 now up to 30 seconds and it still covers applications. I have to kill it manually and restart it.

I did find a thread last night that talked about this issue and someone had an example script doing a loop where it queried something to determine if the time was correct to start conky. Do you think I could find this thread now? nope. So I'm hoping someone knows the post or the script and could post it here for me please. 

Though I would rather if I could just write a script that didn't involve installing yet more software to make it work.

Cheers,

James.

---

### Post by linuxinstalledfromhdd on 2011-05-21
It needs to create it's own window..

Try a different conky script.. until you find one that is preconfigured and gives you the result you are looking for, then compare that script with your old conky script.

That worked for me when I was playing with conky a while ago.

---

### Post by cafejunkie on 2011-05-21
With Nautilus, as the above post says, conky needs to be it's own window.
Also, if it's not already, try setting the "own_window_type" option to "override" that generally works for me. Other options for that variable are:
Desktop
Normal
Dock
Panel

Play around with the settings. 
Also take a look at [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html) that contains all the configuration options available.

---

### Post by linuxinstalledfromhdd on 2011-05-21
thank you, that's what you need to have in that conky script in order for it to create it's own window.  I've played with conky in some time, but it's great.

---

### Post by wildmanne39 on 2011-05-21
> **jamesjenner said:**
> G'day all,

I've been playing and tweeking conky and have got it running quite nicely. I created a script and put a sleep in it at the start with && and then put the script in the startup programs so that it would startup automatically.

Now I have the exact same configuration on a lappy (MacBook 5,1) and it works perfectly, starts up automatically and behaves how I like it. 

On my PC however I've been increasing the delay from 2 now up to 30 seconds and it still covers applications. I have to kill it manually and restart it.

I did find a thread last night that talked about this issue and someone had an example script doing a loop where it queried something to determine if the time was correct to start conky. Do you think I could find this thread now? nope. So I'm hoping someone knows the post or the script and could post it here for me please. 

Though I would rather if I could just write a script that didn't involve installing yet more software to make it work.

Cheers,

James.
Hi, you have to create a bash script like this 
```

conky -p 40 -c ~/.conkyrc &
exit

```Then right click and go to properties and make it executable. you will create it with gedit and you can name it what you want but alot people name it ssc.sh, It does have to end in .sh and it needs to be in the home folder, you will have to click ctrl h to show the hidden files in the home directory then you will be able to see it. Once you do that you go into statrup applications and add it to the startup usually name it conky,and browse to the folder where you put the startup script, so it will have a path to it, then make sure to put a check next to it and your done.

---

### Post by jamesjenner on 2011-05-21
Hey eveyone,

Thanks for your feedback. Maybe I should have been clearer but I have the exact same scripts, configuration, etc on two different systems. Only on one of them do I have the problem where conky is on top, on the other one it never is. So I'm presuming it's not a configuration issue. Also when I take into account that if I kill conky and start it via my script then it works perfectly then I presume it's purely a timing issue.

The script I use is:
```
#!/bin/bash

sleep 20 &&
conky -c ./.conky/.conkyrc &
```I suspect that the script is actually holding up my boot time by 20 seconds, so I'm going to try your version wildmanne39. However I don't know if this will be any different to doing a sleep.

There was a thread and someone had a script with a loop querying the window system as to its state, and only when it reached a certain state would it run conky. Anyone know what that was?

---

### Post by wildmanne39 on 2011-05-21
> **jamesjenner said:**
> Hey eveyone,

Thanks for your feedback. Maybe I should have been clearer but I have the exact same scripts, configuration, etc on two different systems. Only on one of them do I have the problem where conky is on top, on the other one it never is. So I'm presuming it's not a configuration issue. Also when I take into account that if I kill conky and start it via my script then it works perfectly then I presume it's purely a timing issue.

The script I use is:
```
#!/bin/bash

sleep 20 &&
conky -c ./.conky/.conkyrc &
```I suspect that the script is actually holding up my boot time by 20 seconds, so I'm going to try your version wildmanne39. However I don't know if this will be any different to doing a sleep.

There was a thread and someone had a script with a loop querying the window system as to its state, and only when it reached a certain state would it run conky. Anyone know what that was?
HI, let us know how it goes, and I think your script needs the exit at the end.

---

### Post by jamesjenner on 2011-05-21
> **wildmanne39 said:**
> HI, let us know how it goes, and I think your script needs the exit at the end.

Hey mate,

damn good news this morning, looks like your -p option did the trick. Buggered if I know why, I should download the source and see what's going on. 

Basically I changed my script to now read:

```
#!/bin/bash

#sleep 20 &&
conky -p 40 -c ./.conky/.conkyrc &

```

And it worked like a charm! of course 40 is larger than what I had previously been doing so it is possible that increasing sleep to 40 could have had the same result. 

I walked away while it was booting, so I don't know at this point in time if the -p X is delaying the start up, it shouldn't because it's told to run in background.

Hmm. not sure about the comment of using exit. I didn't think exit was required in shell scripts, I've never used one. Is this something to do with the fact that it's a script used during startup?

---

### Post by wildmanne39 on 2011-05-21
> **jamesjenner said:**
> Hey mate,

damn good news this morning, looks like your -p option did the trick. Buggered if I know why, I should download the source and see what's going on. 

Basically I changed my script to now read:

```
#!/bin/bash

#sleep 20 &&
conky -p 40 -c ./.conky/.conkyrc &

```

And it worked like a charm! of course 40 is larger than what I had previously been doing so it is possible that increasing sleep to 40 could have had the same result. 

I walked away while it was booting, so I don't know at this point in time if the -p X is delaying the start up, it shouldn't because it's told to run in background.

Hmm. not sure about the comment of using exit. I didn't think exit was required in shell scripts, I've never used one. Is this something to do with the fact that it's a script used during startup?
Hi, it is possible that the 20 seconds just was not long enough if you are usning natty. Glad it is working, there is more then one way to make it delay.):P

---

### Post by jamesjenner on 2011-05-22
> **wildmanne39 said:**
> Hi, it is possible that the 20 seconds just was not long enough if you are usning natty. Glad it is working, there is more then one way to make it delay.):P

lol, I suspect your right. Just to test I'm going to decrease it and see if it makes a difference. I presume cause it's in the background it wont delay the startup time (which is far more preferable as the sleep X causes a delay).

---

### Post by jamesjenner on 2011-05-24
Startup still delaying so may be something else. To quote the famous Inspector Clouseau would say > "...the case is solve-ed!"

---

### Post by firekage on 2013-01-14
Sorry for refreshing but i have a question - could you tell me where to put, what to put, how to name it, file to delay conky startup?

I use conky but after update from 12.04 to 12.10 when it starts than strange behaviour occurs, conky goes into "white state mode" where i don't see a conky but a wall of white "board' under conky. I have to kill conky, and start it again and it goes just like it should. I think it is related to booting my computer, running serviced during start up and activating desktop or graphic in it.

I would like to delay it but i don't know where to put a file, how to name it and what to place in it - first posts shows something but i'm not sure.

Could you help me? Thanks.

---

### Post by stinkeye on 2013-01-14
> **firekage said:**
> Sorry for refreshing but i have a question - could you tell me where to put, what to put, how to name it, file to delay conky startup?

I use conky but after update from 12.04 to 12.10 when it starts than strange behaviour occurs, conky goes into "white state mode" where i don't see a conky but a wall of white "board' under conky. I have to kill conky, and start it again and it goes just like it should. I think it is related to booting my computer, running serviced during start up and activating desktop or graphic in it.

I would like to delay it but i don't know where to put a file, how to name it and what to place in it - first posts shows something but i'm not sure.

Could you help me? Thanks.
Experienced the same problem in Quantal and was caused by using
```
own_window_type override
```

Try..
```
own_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
```

own_window_type override ignores own_window_hints but
own_window_type normal requires own_window_hints.


To delay the start of conky:
If your conky config is located @ ~/.conkyrc use...
```
conky -p 30
```

If your config is in another location use...
```
conky -p 30 -c [COLOR="Magenta"]/path/to/your/config[/COLOR]
```
Place the relevant command in startup applications.

---

### Post by firekage on 2013-01-16
> **stinkeye said:**
> Experienced the same problem in Quantal and was caused by using
```
own_window_type override
```Try..
```
own_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
```own_window_type override ignores own_window_hints but
own_window_type normal requires own_window_hints.


To delay the start of conky:
If your conky config is located @ ~/.conkyrc use...
```
conky -p 30
```If your config is in another location use...
```
conky -p 30 -c [COLOR=Magenta]/path/to/your/config[/COLOR]
```Place the relevant command in startup applications.

Thanks. I will try this.

BTW - i delayed conky by making .conky_start.sh file in my home folder, than chmod a+x on it, and put there 

```
#!bin/bash
sleep 70 && conky;
```

and it works.

---

### Post by stinkeye on 2013-01-17
> **firekage said:**
> Thanks. I will try this.

BTW - i delayed conky by making .conky_start.sh file in my home folder, than chmod a+x on it, and put there 

```
#!bin/bash
sleep 70 && conky;
```

and it works.
Either way will work. One uses a bash script, the other uses an inbuilt
conky command to delay the start of conky.
You just need to give enough time for the window manager to load.
Usually 20 secs is enough.

In Unity I use a script which wont run conky until the unity-panel-service
is up and running because of the differing load times between a reboot and logout/login.Gets conky running as soon as possible.
```
#!/bin/bash

until (pidof unity-panel-service)
  do
    sleep 2
  done
sleep 2
	conky -c ~/conky/configs/timer-conkyrc &
	conky -c ~/conky/configs/cal-conkyrc &
	conky -c /home/glen/conky/configs/release.conkyrc &
```

---

### Post by firekage on 2013-02-04
> **stinkeye said:**
> Experienced the same problem in Quantal and was caused by using
```
own_window_type override
```Try..
```
own_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
```own_window_type override ignores own_window_hints but
own_window_type normal requires own_window_hints.


To delay the start of conky:
If your conky config is located @ ~/.conkyrc use...
```
conky -p 30
```If your config is in another location use...
```
conky -p 30 -c [COLOR=Magenta]/path/to/your/config[/COLOR]
```Place the relevant command in startup applications.

I wanted to write this earlier but i've been testing so far your setup and following your advice i must say: thank you. 

It works. I changed, in conky, settings that you mentioned, and now conky doesen't change its window, it is not "white wall" anymore.

Thank you again.

---

