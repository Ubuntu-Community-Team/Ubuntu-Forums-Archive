---
title: "Run shell script only when idle?"
date: 2009-08-31
forum: General Help
---

### Post by paradigm2 on 2009-08-31
Hello, I was just researching this and didn't find much in the way of what I wanted.  I have a script which uses a significant amount of resources -- CPU, memory, and I/O and I would only like it to run when the computer is Idle (Say after 15 minutes or whenever the screensaver is on.

ionice and nice unfortunately are not good enough. Using them still makes the system significantly lagging (This computer is already on old hardware).

I saw many solutions which were based on looking at one user's idle time but I noted these are faulty because right now I am logged in four terminals so they gewnerally wouldn't seem to work for me.

Is there not an elegant and easy way to do this?

---

### Post by paradigm2 on 2009-09-01
bump

---

### Post by falconindy on 2009-09-01
Perl has an X11:IdleTime function in the CPAN modules. I suppose you could poll this periodically and if it returns over a set value, continue your script. Found some limited doc on cpan.org:
```
   use X11::IdleTime;[FONT=monospace]
[/FONT]   $idle = GetIdleTime();[FONT=monospace]
[/FONT]   print "Your mouse and keyboard have been idle for $idle seconds.\n";
```

---

### Post by paradigm2 on 2009-09-01
> **falconindy said:**
> Perl has an X11:IdleTime function in the CPAN module. I suppose you could poll this periodically and if it returns over a set value, continue your script. Found some limited doc on cpan.org:
```
   use X11::IdleTime;[FONT=monospace]
[/FONT]   $idle = GetIdleTime();[FONT=monospace]
[/FONT]   print "Your mouse and keyboard have been idle for $idle seconds.\n";
```

Thanks I will look into this more.  I really need it as right now I have it set up only as a cron job from 11pm - 7am but the script is a web crawler and I'd ideally like it running whenever possible (when idle). Also sometimes I use the computer after 11 and it becomes a real pain.  I imagine it might also help people who support projects like SETI or @home.

I hope that perl function looks at the keyboard and mouse universally on the system.  If so it will be perfect.  Another option I guess the crawler is an open source C++ project6 so I guess I could alter the source and use a native C++ function.

---

