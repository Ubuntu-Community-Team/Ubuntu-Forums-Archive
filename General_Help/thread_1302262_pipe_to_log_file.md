---
title: "pipe to log file"
date: 2009-10-26
forum: General Help
---

### Post by ShapeShiftme on 2009-10-26
Good day all.

Im trying to figure out why my wine keeps crashing when running dreamweaver with 2 monitors.

So one thing ive found is that wine does not create a log file. That is kinda annoying but i hear that one can pipe the output to file.

So i have tried the following
1) wine /path-to-app/dreamweaver.exe > /path-to log/log_wine.log
2) wine /path-to-app/dreamweaver.exe | tee /path-to log/log_wine.log

With both theese options i have a file but the stpid thing is empty. Can someone please tell mee what im doing wrong and perhaps give me some advise to put me in the right direction.

Regards
Donovan Hoare

---

### Post by Giblet5 on 2009-10-26
> **ShapeShiftme said:**
> Good day all.

Im trying to figure out why my wine keeps crashing when running dreamweaver with 2 monitors.

So one thing ive found is that wine does not create a log file. That is kinda annoying but i hear that one can pipe the output to file.

So i have tried the following
1) wine /path-to-app/dreamweaver.exe > /path-to log/log_wine.log
2) wine /path-to-app/dreamweaver.exe | tee /path-to log/log_wine.log

With both theese options i have a file but the stpid thing is empty. Can someone please tell mee what im doing wrong and perhaps give me some advise to put me in the right direction.

Regards
Donovan Hoare


Try: ```
wine /path-to-app/dreamweaver.exe > /path-to log/log_wine.log 2>&1
```

There are three stdio streams:
stdin = standard input
stdout = standard output
stderr = standard error

These are file descriptors 0, 1, and 2, respectively.

< and << redirect standard input
> and >> redirect w/ overwrite or redirect w/ append the stdout stream
2> and 2>> redirect w/overwite or redirect with append the stderr stream

2>&1 = send the stderr stream to wherever stdout is going

---

### Post by undecim on 2009-10-26
Both of those will redirect stdout, but not stderr 

try```
 wine /path-to-app/dreamweaver.exe 2> /path-to log/log_wine.log
```

---

### Post by ShapeShiftme on 2009-10-26
OK i have to be really stupid.

Neither of the above commands suggested actually gave any (none,zip nada, nothing) in output logfile.

Whe i run the command in terminal i see the ouput (stanadrad wine /pathto file/)

But none of that displays. Does anyone have anyother sugestions on what im doing wrong.

Regards
Donovan Hoare

---

### Post by ShapeShiftme on 2009-10-26
Perhaps that i should mention. 
After a few seconds when running the command my machine crashes. For 1 sec i can see the login screen of tty1. and that its. (as if kde died) Hung i have to hard reboot the laptop. So if theese commands require the process to finish or yakes time bore writing to file that is not going to work.

Regards
Donovan Hoare

---

### Post by Giblet5 on 2009-10-26
The "> filename 2>&1" *will* work, but wine may need to perform a normal exit before you see the output in the file.

Your system isn't crashing...just the GUI software (Xorg).

It can take a few seconds to restart on its own.

The Xorg server is crashing because of something wine is trying to do that conflicts with Xorg. Probably a bug.

If you're running compiz, you might have to turn it off to use this application (that is common with wine). Click System -> Preferences -> Appearance. Select the Effects tab. Select None.

Then try the wine app again.

OK... KDE then. Can you run a gnome session with compiz turned off for this wine application? KDE is ... demanding on the graphics subsystem. I have had no luck using wine under KDE.

---

### Post by ShapeShiftme on 2009-10-26
Desktop effects has a tick in it but is disabled (Grayed out). 

Just to let you know dreamweaver works fine when i only have 1 monitor attached. When i have 2 it dies. So i was gathering ATI drivers.

But i wanted to know what wine says when it happens. It happens very Quickly but the last line i can read says audio something.

So it might even be that the monitor im using uses HDMO and there for ATI HDMI audio.. That might have something to do with it.

Perhaps ill go buy a normal VGA cable and try that so audio is not enabled.

For the time being it there no way to pipe information to a file without a normal exit

Regards
Donovan Hoare

---

### Post by Giblet5 on 2009-10-26
The problem is that wine is buffering the output. When it is forced to exit by the Xorg crash, it hasn't flushed those buffers.

It's hard coded to buffer, I'm afraid. That is VERY non-standard, but I don't feel like rewriting it... :)

Here's a way that you *might* get something useful out of it:
```
export WINEDEBUG="warn+all"
wine /path-to-app/dreamweaver.exe > /tmp/dreamweaver.log 2>&1
```

That'll turn on all the bells and whistles...

Those buffers are only 4KB or so. ;)


Note: I found other links relating to this...with ATI drivers.

You might have to switch to single-screen while using dreamweaver. :(

---

### Post by ShapeShiftme on 2009-10-27
No luck to the wicked.

I stole my wife's VGA cable. And that didnt work.

I tries the export thing. (I'm gathering it is 2 separate commands)
That didnt work either.

In another post i was asked to make the screen smaller. (Not maximised)
As dreamweaver works with only one monitor. But to no avail

So mean bugger (Murphy) is telling me to use windows and I DON'T want to.

Stumped i am.

Any other ideas.

Regards
Donovan Hoare

---

### Post by Giblet5 on 2009-10-27
This system boots 4 flavors of Linux, plus WinXP-32, Vista-64, and Win7-64.

Sometimes - not often - Windows is the better place to run Windows software.

Examples: P-shop, Premiere, and 3DSMAX.

Call Adobe sometime and ask them how to get P-shop CS4 running under wine. At least *I* didn't yell at you. ;)

---

### Post by ShapeShiftme on 2009-10-27
Well Thanks for all your help.

 Hopefully whatever is causing the problem will fix itself over time in updates. Either wine or ATI. not that i know what the problem is. 

So for the time being im running  virtualbox. that runs my dreamweaver And Visual Studio 2008.

Actually using virtual box gives me what i want. I run virtual box on one monitor maximized with dreamweaver. Then i run all the other apps on the other monitors. and with the guest software installed the mouse flows seemlessly. 

Not the best solution. But He it Works.

Regards
Donovan Hoare

---

