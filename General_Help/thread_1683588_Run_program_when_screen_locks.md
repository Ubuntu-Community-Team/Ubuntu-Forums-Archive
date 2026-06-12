---
title: "Run program when screen locks"
date: 2011-02-07
forum: General Help
---

### Post by geometrikal on 2011-02-07
Hi,

I would like to run a command when the screen locks, and another when it unlocks. Does anyone know how to do this?

Why: I work in a shared office space. When I leave my desk (and the screen locks) I would like the webcam motion capture software 'motion' to run, in order to record anyone who uses my computer when I'm gone. Likewise when I come back and unlock the screen I would like it to pause.

cheers

---

### Post by geometrikal on 2011-02-07
Found the answer at:

[http://superuser.com/questions/205334/how-do-you-get-ubuntu-to-automatically-run-a-program-every-time-the-screen-is-unl](http://superuser.com/questions/205334/how-do-you-get-ubuntu-to-automatically-run-a-program-every-time-the-screen-is-unl)

My script is:

```

#!/usr/bin/perl

# Pause motion
system("/usr/bin/lwp-request http://localhost:8080/0/detection/pause > /dev/null");

# Start monitoring dbus
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='ActiveChanged'\"";

open (IN, "$cmd |");

# Loop checking for screen lock
while (<IN>) {
    if (m/^\s+boolean true/) 
    {
        print "*** Screen locked ***\n";
	system("/usr/bin/lwp-request http://localhost:8080/0/detection/start > /dev/null")
    } elsif (m/^\s+boolean false/) {
        print "*** Screen unlocked ***\n";
	system("/usr/bin/lwp-request http://localhost:8080/0/detection/pause > /dev/null")
    }
}

```

---

