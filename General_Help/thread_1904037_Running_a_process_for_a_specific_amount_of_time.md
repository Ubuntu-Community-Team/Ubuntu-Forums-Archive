---
title: "Running a process for a specific amount of time"
date: 2012-01-03
forum: General Help
---

### Post by rsgys on 2012-01-03
Hello,

I'm running experiments with the same process (lets call it foo) on hundreds of data sets. I've run into data sets that are intractable, so I'd like to stop foo after t seconds.

I was instructed to use [alarm]("http://linux.die.net/man/3/alarm"), but I don't have this command on my Ubuntu desktop. I would have used it in the following way:

alarm t foo data

(actually, I'd be running sudo chrt -f 99 alarm ...)

I want to be able to send a signal to foo that I can handle using <csignal>.

So, my question(s):
1) is it possible to install alarm? Ubuntu recommends I install toshutils to obtain alarm, but this is a different program.
2) is there an easier way to do this without alarm? I'd like to incorporate this into a script I've written so I can run all of my experiments with the push of a button.

---

### Post by dcstar on 2012-01-04
[http://ubuntuforums.org/showthread.php?t=1368856](http://ubuntuforums.org/showthread.php?t=1368856)

Or install the **timelimit** package.

---

