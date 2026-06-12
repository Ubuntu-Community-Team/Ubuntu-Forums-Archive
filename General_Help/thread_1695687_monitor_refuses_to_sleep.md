---
title: "monitor refuses to sleep"
date: 2011-02-26
forum: General Help
---

### Post by tobydog on 2011-02-26
hi i have my pc set for the monitor to sleep after 15min of no use it refuses to do so , it goes to the screen saver ok but will not sleep , does anyone have any idea how i can fix this please.my pc is a packard bel 5118 pentium 4 512mb ram monitor is hanns-g 28" lcd

---

### Post by tobydog on 2011-03-02
hi again still have this problem , its realy anoying and is wearing out my monitor on off switch please does anyone have any ideas how to make my monitor settings for sleeping work.:confused:

---

### Post by grahammechanical on 2011-03-02
Does the monitor itself have a settings program? Can you bring up a menu on the monitor independent of operating system? You may have power saving features disabled.

Regards.

---

### Post by tobydog on 2011-03-07
just checked the monitor menu and doesn't appear to have a setting for this so its not the problem, i still need help sorting this out please as its a very annoying problem:confused:

---

### Post by pqwoerituytrueiwoq on 2011-03-07
```
xset dpms force off
```
should turn the screen off 
does it work?

---

### Post by no2498 on 2011-03-08
keeping an eye on this 1 mines doing the same thing

---

### Post by tobydog on 2011-03-09
xset dpms force off does work and turns the screen of , now how do i get this to work automaticly as set in my screen power management

---

### Post by pqwoerituytrueiwoq on 2011-03-09
maybe a cron job can do it on idle or something

---

### Post by no2498 on 2011-03-10
thats why i did not try it yesterday
my time here resets to 0 if the screen saver comes on

---

### Post by tordeu on 2011-03-10
There is a thread [here ]("http://ubuntuforums.org/showthread.php?t=1213325")about running a program when the gnome screensaver starts and kill it when it stops. You could try to modify it for your needs, so that it runs the command when it detects the screensaver. So, based on the script from the thread maybe something like this:

```

#!/usr/bin/perl
my $cmd = q[dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'"];
open (IN, "$cmd |");
while (<IN>) {
    if (/^\s+boolean true/) {
        system 'xset dpms force off';
    }
}

```

I am not familiar with perl, but I think there should be a wait or sleep added, so that the script does not use a significant amount of cpu and if we get the script working, you could make it start automatically when you login.

---

### Post by pqwoerituytrueiwoq on 2011-03-11
> **tordeu said:**
> There is a thread [here ]("http://ubuntuforums.org/showthread.php?t=1213325")about running a program when the gnome screensaver starts and kill it when it stops. You could try to modify it for your needs, so that it runs the command when it detects the screensaver. So, based on the script from the thread maybe something like this:

```

#!/usr/bin/perl
my $cmd = q[dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'"];
open (IN, "$cmd |");
while (<IN>) {
    if (/^\s+boolean true/) {
        system 'xset dpms force off';
    }
}

```I am not familiar with perl, but I think there should be a wait or sleep added, so that the script does not use a significant amount of cpu and if we get the script working, you could make it start automatically when you login.
i am not eigher but if you see the line that turns the screen off it clearly runs a system command so in theory you can put sleep 600 before it
```

#!/usr/bin/perl
my $cmd = q[dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'"];
open (IN, "$cmd |");
while (<IN>) {
    if (/^\s+boolean true/) {
        system 'sleep 600; xset dpms force off';
    }
}

```
there is a while loop in it i am not shure if it loops through monitors or what but the sleep 600 may make it take longer to finish hopefully there is only instance that passes the if test as the system function probally waits for the commend to finish

---

### Post by tordeu on 2011-03-11
Argh!  #-oOf course. I don't know why I didn't think of just calling sleep from perl instead of wanting to use a perl sleep function. I guess I was up too late. Thanks for hint.

I hope this fixes tobydog's problem now.

---

