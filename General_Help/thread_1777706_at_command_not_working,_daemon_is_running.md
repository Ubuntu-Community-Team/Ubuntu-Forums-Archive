---
title: "at command not working, daemon is running"
date: 2011-06-08
forum: General Help
---

### Post by apa0apa on 2011-06-08
Hello
I run Ubuntu 10.04 LTS. 
I have a problem with "at" command not working. 
I have used it for ages with no problem. Suddenly it appears not to work anymore.
Atd daemon is running. 

Examples: 
$ echo "ciao" | at now
warning: commands will be executed using /bin/sh
job 346 at Wed Jun  8 09:39:00 2011

It does nothing. Same if I use sudo. 

$ at 9:41
warning: commands will be executed using /bin/sh
at> echo "ciao"
at> <EOT>
job 347 at Wed Jun  8 09:41:00 2011

Does nothing again. 

Daemon: 

$ ps -elf | grep atd
5 S daemon    2188     1  0  80   0 -  4722 hrtime 09:18 ?        00:00:00 atd
0 S antonio   2728  1914  0  80   0 -  1907 pipe_w 09:41 pts/0    00:00:00 grep atd

Thanks for any help
antonio

---

### Post by hakermania on 2011-06-08
Hello, i executed myself
```
echo "Hello" | at now
``` and did nothing, I've never used 'at' before because I use 'sleep', but it seems that 'at' makes the process backround and redirects the output somewhere else, not in the current terminal, while the commands really run. For example, if you give
```
echo "Hello" > ~/Desktop/HelloFile | at now
``` it WILL create a file named HelloFile with the content 'Hello' in your Desktop.
And
```
gedit | at now
``` will execute gedit now :)

---

### Post by apa0apa on 2011-06-08
Thanks hakermania

This works:

gedit | at now
But this: 

$ gedit | at 9:55

launchs gedit, but not at 9:55 but immediately

And this does nothing again:

$at 9:56
warning: commands will be executed using /bin/sh
at> gedit
at> <EOT>
job 351 at Wed Jun  8 09:56:00 2011

---

### Post by hakermania on 2011-06-08
same problem here :/

---

### Post by gmargo on 2011-06-08
I see there is some confusion about how to use the **at(1)** command.  Several of the things you tried were correct, however you came to the incorrect conclusion that **at** was not working.

The important thing to remember about **at** or **cron** jobs is that they run in a sanitized environment.  They cannot access the screen without jumping through some extra hoops, and they cannot write text to your terminal window.  The output from at/cron jobs will be emailed to you (unless you redirect the output).

If you have an MTA installed (such as postfix or exim4), then you will receive the email.  If you do not have an MTA installed, then the output goes to the bit bucket.  Check your log files (/var/log/syslog).  You will probably see a message that says something like (this is from memory): CRON: no MTA installed, discarding output.

Here's the exact message you'll see in the log if the at daemon cannot find an MTA:
```

atd[pid]: Exec failed for mail command: No such file or directory

```So the first thing you should do is install an MTA so that you can receive locally generated email.


Now, on to your examples:
> 
```

$ echo "ciao" | at now
warning: commands will be executed using /bin/sh
job 346 at Wed Jun  8 09:39:00 2011

```This will work.  However, the at daemon attempts to execute a program named "ciao".  Then it sends you an email that says it can't find "ciao".  Remember that the "echo" here runs in your current shell (not the at daemon shell).

> 
```

$ at 9:41
warning: commands will be executed using /bin/sh
at> echo "ciao"
at> <EOT>
job 347 at Wed Jun  8 09:41:00 2011

```This will work.  The at daemon executed the echo command and the "caio" is sent to the standard output, which is then emailed to you.


And now here's the hoop you need to get **gedit** to work.  Since the environment has been sanitized, it does not have the $DISPLAY variable that it needs.  The following will work:
```

$ at now
warning: commands will be executed using /bin/sh
at> env DISPLAY=:0 gedit
at> <EOT>

```

---

### Post by hakermania on 2011-06-09
Thanks gmargo, really useful info :)
Personally I didn't know a lot about at but now I do know a few things :)

---

### Post by apa0apa on 2011-06-10
Thanks a lot.
Everything is clear now and yes, the problem is solved.
Thanks again

---

