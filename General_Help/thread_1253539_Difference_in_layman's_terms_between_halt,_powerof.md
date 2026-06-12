---
title: "Difference in layman's terms between halt, poweroff, and shutdown."
date: 2009-08-30
forum: General Help
---

### Post by mibbster on 2009-08-30
Okay, so I'm running Ubuntu Server 8.04.3, and I can't turn off my machine.  I've been using ```
sudo shutdown now
``` to do it.  What always happens is that the system goes down for a moment, then, almost immediately, it boots back up into a ["recovery menu"]("http://www.geeksquadwiki.com/gsw/images/e/ef/UbuntuReset6.jpg").  I then need to do a hard power-off each time.  I'm aware this isn't very healthy for the computer and it hard drive, and its by no means ideal.  Does anyone know why this is and how to fix it?  Am I doing it wrong?  At first I thought it must be a problem with my system, but now I'm starting to think I may be trying to do it incorrectly.  My googling has led me to learn that there are actually three separate commands: halt, poweroff, and shutdown.  What is the relationship between the three?  What's the difference?  Are any replaceable with options from another?  Which one of them should I be using?  Maybe they do different things, so if that's the case, you'll need to know what my objective is:

I need the most straightforward, comprehensive, safe, versatile one.  It would be nice if it could be called from scripts and cronjobs as well.  shutdown seems to actually notify all the users that the system is shutting down, which is nice.  It also gives all of my processes a friendly SIGTERM warning.  If there was one that made sure my hard drive turned off in the way that means the least risk of damage, that would be good to know as well.

I basically need someone to recommend me a command to use for routinely shutting down the machine (I've looked at the manpages for each, but found them hard to understand and follow.), and if possible, explain to me in simple terms what each one does.  Thanks so much in advance!!

P.S.  Please pardon the bad english, its my second language and I'm still learning. :)

---

### Post by dearingj on 2009-08-30
Here's what I've been able to figure out, just from exploring my own system right now and reading one man page:
[LIST]
[*]The shutdown program is able to poweroff or reboot your system, depending on which arguments you pass to it. (-h to poweroff or -r to reboot)
[*]The reboot command just calls 'shutdown -r', unless you type in 'reboot --force' in which case it reboots the system itself
[*]The halt and poweroff commands appear to be aliases for reboot
[/LIST]

In other words, if you want to shutdown your system you enter 'sudo shutdown -h now', and if you want to reboot you enter 'sudo shutdown -r now'

---

### Post by unutbu on 2009-08-30
mibbster, it sounds like your machine is having a shutdown problem. 
Perhaps take a look at [this post]("http://ubuntuforums.org/showpost.php?p=6176637&postcount=28"), which describes some solutions to shutdown problems.
Since shutdown problems have a few different causes, there are correspondingly a few solutions. It takes some experimentation to find out which one (if any) works for you. 

The first one (stopping networking) doesn't sound like your situation.
The second (acpi=force) may be worth a try
The third (apm power_off=1) is also worth a try, especially if your server is a couple of years old.

---

### Post by tgeer43 on 2009-08-30
Dearingj's commands are quite correct.

Just FYI here is the technical difference (in layman's terms) between halt, poweroff, and shutdown:

Halt essentially 'shuts down' the operating system.
Poweroff is the same as halt but also powers off the machine.
Shutdown is the same as poweroff but exits more correctly by executing the shutdown scripts in /etc/rc0.d.

So you can see why shutdown is the preferred method.

tgeer

---

### Post by mibbster on 2009-08-30
@tgeer43 so can you just confirm two things for me then?  

a) in general (i.e. not taking into consideration the problem that I've been having) shutdown should be the preferred method of turning off the computer? and 

b) you need to use either the -h option of the -p option for it to actually doing anything?  In other words, by not using either, I've been doing it wrong all this time?

@unutbu see point b) above.  If it is, in fact, correct, wouldn't that mean that my "shutdown problem" is just that I've been using the wrong command?  Is this what the problem is?  If so, then why did you provide me with other troubleshooting options?  Sorry, not trying to sound accusatory, I'm just a little confused.  Thanks, everyone!

P.S. Is it just me, or does "halt" sound a little violent?

---

### Post by unutbu on 2009-08-30
Sorry, mibbster. I was mistaken. Your symptoms are not that of a shutdown problem.
I just tried the
```

sudo shutdown now 
```

command, and after stopping a bunch of services, the machine went to the recovery menu.
I didn't know that's what happened.

dearingj gave the correct command:
```

sudo shutdown -h now
```

"shutdown -h now" is the preferred method of turning off the machine.

If you run "/sbin/halt" then no shutdown scripts are run. This is violent. 
If you run "shutdown -h now" then the shutdown scripts (in /etc/rc2.d and /etc/rc0.d) are run. Once they are done, then the machine is halted. This is gentlest and safest.

---

### Post by mibbster on 2009-08-30
Okay, thanks so much!

---

### Post by mibbster on 2009-08-31
Okay, for future googlers, I've actually done some more research and figured I would post the links I found useful.  First some SEO... :)


what is the difference between halt, poweroff, and shutdown?

halt, poweroff, shutdown explanation

okay, that was a little stupid, but whatever. :)

[http://www.linuxforums.org/forum/linux-newbie/146272-difference-between-poweroff-shutdown-h-now-2.html](http://www.linuxforums.org/forum/linux-newbie/146272-difference-between-poweroff-shutdown-h-now-2.html)
[http://www.oreillynet.com/linux/cmd/cmd.csp?path=p/poweroff](http://www.oreillynet.com/linux/cmd/cmd.csp?path=p/poweroff)
[http://ubuntuforums.org/archive/index.php/t-1012204.html](http://ubuntuforums.org/archive/index.php/t-1012204.html)
[http://manpages.ubuntu.com/manpages/karmic/en/man8/poweroff.8.html](http://manpages.ubuntu.com/manpages/karmic/en/man8/poweroff.8.html)
[http://manpages.ubuntu.com/manpages/karmic/en/man8/shutdown.8.html](http://manpages.ubuntu.com/manpages/karmic/en/man8/shutdown.8.html)

for those wondering what "halt" means, apparently its like the technical term for "standby" or "sleep" mode.



For those just wondering what the correct way to shut down the system without a GUI is, it's
```

sudo shutdown -h now

```

---

### Post by mibbster on 2009-08-31
Wait...

Now that I'm reading through the manpage for shutdown with some new understanding, shouldn't I be using 
```

sudo shutdown -hP now

```
based on what I want to do?  Why wasn't the -P option recommended to me as well?
THanks.

---

### Post by lykwydchykyn on 2009-08-31
Actually, on debian (and hence ubuntu) systems, if you just run "halt" it will simply call shutdown -h, so it's not violent (unless you add the -f switch, which will literally halt).

If you don't believe me, see "man halt".

---

### Post by mibbster on 2009-08-31
So should I, or should I not be using the -P option?

---

### Post by unutbu on 2009-08-31
According to the shutdown man page:
```

       -h     Requests that the system be either halted or powered off after it has been
              brought down, **with the choice as to which left up to the system**.

       -P     Requests that the system be powered off after it has been brought down.

```


On my machine

"shutdown -h now" powers off the system. So I expect that
"shutdown -P now" would be no different.

---

### Post by tzihad on 2009-09-17
On my machine
"shutdown -h now" Leaves power button lighted and usb keyboard powered.
only "shutdown -P now" shuts down machine completely.

---

