---
title: "How to View Command Sent Previously"
date: 2012-05-12
forum: General Help
---

### Post by scambro on 2012-05-12
HI all,

I executed a script via the terminal on my Ubuntu box a few hours ago.  I thought I had done that in a screen session, but evidently not.  Now I'm signing in via SSH and I don't see the log file that I thought I sent in the command.  So I started this script which will take a few hours to run, but all the output, is going somewhere else.  I must have typo'd the name when I kicked it off. 

Is there anyway to see what the command was that triggered a PID?  It's still going, and I can see the script name in htop, but not much else. 

Thanks!

---

### Post by sudodus on 2012-05-12
Try ```
ps -AF
``` for a long list of all commands or 
```
ps -AF | grep name-of-the-command
``` if you know the name or part of the command name

*Edit: By the way, if you run htop in a **[I]full-screen terminal window***, you might see enough of the command name[/I]

---

### Post by codemaniac on 2012-05-12
> **scambro said:**
> HI all,

I executed a script via the terminal on my Ubuntu box a few hours ago.  I thought I had done that in a screen session, but evidently not.  Now I'm signing in via SSH and I don't see the log file that I thought I sent in the command.  So I started this script which will take a few hours to run, but all the output, is going somewhere else.  I must have typo'd the name when I kicked it off. 

Is there anyway to see what the command was that triggered a PID?  It's still going, and I can see the script name in htop, but not much else. 

Thanks!

If you have run the script in background , it would run as a job under the hood .
```
jobs
```

---

### Post by scambro on 2012-05-12
> **sudodus said:**
> Try ```
ps -AF
``` for a long list of all commands or 
```
ps -AF | grep name-of-the-command
``` if you know the name or part of the command name

*Edit: By the way, if you run htop in a **[I]full-screen terminal window***, you might see enough of the command name[/I]

When I run ps -AF, i see the command, but it's just telling me it's running, much in the same was as htop:

```

PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command                                                                                                                                         
 20   0 77040  8728  4200 S  0.0  0.9  3:08.81  `- gnome-terminal               
 20   0  7856  1992   972 S  0.0  0.2  0:01.68  |   `- bash               
 20   0  7584  3420  1816 D  3.0  0.3 28:09.01  |   |   `- /usr/bin/perl -w /usr/local/bin/md5check

```

** codemaniac** - nothing shows when I run jobs, so I'm guessing that means it isn't running in the background.  Not sure exactly what you mean by that though, so I'll have to check that out for the future. 

Thanks!

---

### Post by sudodus on 2012-05-12
I don't understand what you want.

---

### Post by scambro on 2012-05-12
> **sudodus said:**
> I don't understand what you want.

When I executed this command, I should have typed "md5check > ../logfile.log".  That way, I can read all of the output during and after execution.  I SSH'd in from another location and I do not see logfile.log, so I'm assuming I typed something else in, like md5check > ..logfile.log, ../../logfile, etc.  But I can't find it just by doing a quick search.

I was hoping to be able to figure out the exact command that was entered at the terminal, including the "> logfile.log" part.

Thanks!

---

### Post by flemur13013 on 2012-05-12
$ history

---

### Post by scambro on 2012-05-12
> **flemur13013 said:**
> $ history

That doesn't seem to cross terminal sessions though.  For instance, in my SSH session, I have screen running, and I get different results with history, inside and outside of screen.  

This is a good tip though, I often forget about history and fumble through the up and down arrows trying to find the right command...

Thanks!

---

### Post by codemaniac on 2012-05-12
"jobs" lists the jobs that you are running in the background and in the foreground. If the prompt is returned with no information no jobs are present. 
I suspected if the script would take hours to take then you might have run in the background .

---

### Post by sudodus on 2012-05-12
If you have a feeling that the file name contains log, try

```
sudo find / -name "*log*" -ctime -1 -type f | sort
```
to find files containing 'log' everywhere (/) changed during the last 24 hours

If you know it was written within your user account, then use```
sudo find ~ -name "*log*" -ctime -1 -type f | sort
```

[I]Edit: Modify if there are too many files, for example
use -cmin instead of -ctime (minutes instead of days)
use *.log if you know the file had the extension log
etc[/I]

---

### Post by scambro on 2012-05-12
> **sudodus said:**
> If you have a feeling that the file name contains log, try

```
sudo find / -name "*log*" -ctime -1 -type f | sort
```
to find files containing 'log' everywhere (/) changed during the last 24 hours

If you know it was written within your user account, then use```
sudo find ~ -name "*log*" -ctime -1 -type f | sort
```

[I]Edit: Modify if there are too many files, for example
use -cmin instead of -ctime (minutes instead of days)
use *.log if you know the file had the extension log
etc[/I]

Thanks for the help.  I wasn't able to find it this way, so perhaps I screwed up the command enough that's it's still logging to the terminal.  Oh well.  This was helpful info that I'll keep in my back pocket until I have a need to use it again. 

Thanks!

---

