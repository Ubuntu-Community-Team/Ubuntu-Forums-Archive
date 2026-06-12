---
title: "Program exits itself"
date: 2010-05-14
forum: General Help
---

### Post by DreamShardDev on 2010-05-14
I have been using Retroshare a lot recently and a day or so I must have done something that suddenly wrecked it because now the program terminates automatically after 10 secs or so. Now I have tried rebooting, re-installing, upgrading and all sorts of bug checks for the program and nothings changed and right now my best guess is that there is something that i have done which terminates the Retroshare process a certain amount of time after it opens. Is there anything I can do to see what is causing this program to quit ? Or to diagnose what is the cause of the problem. If i knew why it was exiting i could probably figure out how to fix this. Thanks and any help would be appreciated :guitar:

---

### Post by rnerwein on 2010-05-14
hi
if there is no diagnostic file then you can try the commands: strace and ltrace.
for both of them there is a huge output. see: man strace / ltrace
you can start your process in a terminal in the following matter:
strace -ff -o logfile.log /path_to_your_process/rtroshare
in short: ff told the trace to following forks, -o means a logfile with the given name.
in that logfile, near the end you will see something like " received signal" or "SIGSEGV" ....
post the ziped logfile. i'll see what i can read from it.
ciao

---

### Post by DreamShardDev on 2010-05-14
When I typed in strace -ff -o logfile.log/usr/bin/RetroShare
i got usage: strace [-dffhiqrtttTvVxx] [-a column] [-e expr] ... [-o file]
              [-p pid] ... [-s strsize] [-u username] [-E var=val] ...
              [command [arg ...]]
   or: strace -c -D [-e expr] ... [-O overhead] [-S sortby] [-E var=val] ...
              [command [arg ...]]
-c -- count time, calls, and errors for each syscall and report summary
-f -- follow forks, -ff -- with output into separate files
-F -- attempt to follow vforks, -h -- print help message
-i -- print instruction pointer at time of syscall
-q -- suppress messages about attaching, detaching, etc.
-r -- print relative timestamp, -t -- absolute timestamp, -tt -- with usecs
-T -- print time spent in each syscall, -V -- print version
-v -- verbose mode: print unabbreviated argv, stat, termio[s], etc. args
-x -- print non-ascii strings in hex, -xx -- print all strings in hex
-a column -- alignment COLUMN for printing syscall results (default 40)
-e expr -- a qualifying expression: option=[!]all or option=[!]val1[,val2]...
   options: trace, abbrev, verbose, raw, signal, read, or write
-o file -- send trace output to FILE instead of stderr
-O overhead -- set overhead for tracing syscalls to OVERHEAD usecs
-p pid -- trace process with process id PID, may be repeated
-D -- run tracer process as a detached grandchild, not as parent
-s strsize -- limit length of print strings to STRSIZE chars (default 32)
-S sortby -- sort syscall counts by: time, calls, name, nothing (default time)
-u username -- run command as username handling setuid and/or setgid
-E var=val -- put var=val in the environment for command
-E var -- remove var from the environment for command
 which command do i do ??
Also just a point that may clarify things when i run /usr/bin/RetroShare
the bit where it closes seems to be at 

MessagesDialog::insertMessages calledMessagesDialog::insertMessages()
Current Row: -1
p3Config::backedUpFileSave()  fopen failed for file:/home/dreamshard/.retroshare/(insert id here)/peers.cfg
Segmentation fault

thanks heaps for helping

---

### Post by rnerwein on 2010-05-14
hi
space is missing between the logfile name and your command path.
try again, may be i can see why the file :/home/dreamshard/.retroshare/17a397b6293655bgf5860576965bdc03cb/peers.cfg
couldn't be opend ( no path, permission denied .... ) will see it in the logfile.
good luck
ciao

---

### Post by DreamShardDev on 2010-05-14
-

---

### Post by rnerwein on 2010-05-14
hi
that's not the output of strace but: see -->[COLOR=Red] Invalid Certificate [COLOR=Black]the output you post.[/COLOR]
[COLOR=Black]but to much information in it !!! 

ciao
[/COLOR][/COLOR]

---

### Post by DreamShardDev on 2010-05-14
So where is the outpost that i need to post ??

---

