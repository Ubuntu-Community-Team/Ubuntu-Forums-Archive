---
title: "Measure memory usage of a command?"
date: 2011-12-12
forum: General Help
---

### Post by Kdar on 2011-12-12
Is there a way to measure memory usage of a single command run in terminal? I am thinking of something equivalent to 'time' except for measuring memory usage.

For example.. if I use 'time':
time gzip file.html
Outputs for me time that it takes to do this task.

Is there something to measure memory usage in same way?

---

### Post by nothingspecial on 2011-12-13
Moved to General Help.

---

### Post by Lars Noodén on 2011-12-13
If you take a closer look at [time](http://manpages.ubuntu.com/manpages/oneiric/en/man1/time.1.html), you'll see that there are measurements like RAM and other resources.

---

### Post by Dave_L on 2011-12-13
Thanks for pointing out that the "time" command can produce additional information about resource utilization.

But I found that I had to use the full path /usr/bin/time to get the command options to work. Maybe "time" is aliased somewhere, at least in my case.  I'm just mentioning this in case someone else encounters the same issue.

```
$ time -v echo "Hello, World"
-v: command not found

real	0m0.679s
user	0m0.548s
sys	0m0.128s
```

```
$ /usr/bin/time -v echo "Hello, World"
Hello, World
	Command being timed: "echo Hello, World"
	User time (seconds): 0.00
	System time (seconds): 0.00
	Percent of CPU this job got: 18%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 0:00.04
	Average shared text size (kbytes): 0
	Average unshared data size (kbytes): 0
	Average stack size (kbytes): 0
	Average total size (kbytes): 0
	Maximum resident set size (kbytes): 2432
	Average resident set size (kbytes): 0
	Major (requiring I/O) page faults: 1
	Minor (reclaiming a frame) page faults: 199
	Voluntary context switches: 3
	Involuntary context switches: 2
	Swaps: 0
	File system inputs: 64
	File system outputs: 0
	Socket messages sent: 0
	Socket messages received: 0
	Signals delivered: 0
	Page size (bytes): 4096
	Exit status: 0
```

---

### Post by Lars Noodén on 2011-12-13
I have to use the full path, too, on my system (Precise) to use the custom formats.  I'm not sure if that is a bug or not.

---

### Post by Dave_L on 2011-12-13
I noticed this in the man page:

> Users of the bash shell need to use an explicit path in  order  to  run
       the  external time command and not the shell builtin variant. On system
       where time is installed in /usr/bin, the first example would become
            /usr/bin/time wc /etc/hosts

In the dash shell, the full path is not needed:

> $ dash
$ time -v echo "Hello, World"
Hello, World
	Command being timed: "echo Hello, World"
	User time (seconds): 0.00
	... (truncated output for posting purposes)
	Page size (bytes): 4096
	Exit status: 0

---

### Post by Lars Noodén on 2011-12-13
I would have never suspected that bash had a built-in time command.

---

