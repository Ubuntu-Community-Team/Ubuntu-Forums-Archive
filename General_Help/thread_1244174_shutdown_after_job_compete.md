---
title: "shutdown after job compete"
date: 2009-08-19
forum: General Help
---

### Post by cholericfun on 2009-08-19
Hi,
i haven't been very good at searching for a solution to this
only found a few loose threads that didnt really answer the questioin:


i'm off for a few days but would like to give my computer a really big job to do which would take about 1 day. 

i would like the machine to power off afterwards instead of sitting around wasting power.

```
shutdown -hP +time
``` i know about - what i want here is something along the lines of ```
shutdown -hP +job_complete

```

any ideas?
thanks!

---

### Post by pmlxuser on 2009-08-19
write a script for your jobs
ie
```

$nano jobscript

#! /bin/sh
job 
sudo /sbin/shutdown -h now



```
save the fire
```

$ chmod +x jobscript

```

and run the script
```

$ ./jobscript

```

The trick here is to know the command for running your job say you want to update system

then
job = sudo apt-get upgrade

you will be required t supply password after the process start then you can leave if because the shutdown command will run after job =finished.

---

### Post by McNils on 2009-08-19
It is simple.
This assumes that you run yourjob as root
```
yourjob && shutown -h now
```
Othervise you can configure sudo to allow you to shutdown without password.

---

### Post by mcduck on 2009-08-19
> **pmlxuser said:**
> write a script for your jobs
ie
```

$nano jobscript

#! /bin/sh
job 
sudo /sbin/shutdown -h now



```
save the fire
```

$ chmod +x jobscript

```

and run the script
```

$ ./jobscript

```

The trick here is to know the command for running your job say you want to update system

then
job = sudo apt-get upgrade

you will be required t supply password after the process start then you can leave if because the shutdown command will run after job =finished.

wouldn't that actually ask for password after the job has finished? THe "sudo" isn't execueted before that.. ;)

A trick to solve the problem, while still running the actual job as normal user, would be to use sudo's ability to run things as any user, not just root:

```
#! /bin/sh
sudo -u cholericfun job 
halt
```

Now run the script with "sudo ./yourscript", and type your password. It will start the job as the user specified,  and when done run the shutdown command which won't require password any more (you already gave it when you started the script)

---

### Post by cholericfun on 2009-08-19
Hi,
thanks for the replies!

didnt think of just writing a sequential script - that is really an easy solution. thanks a lot for the examples and pointing out the pitfalls (never looked into bash that much).

gonna do a testrun in a bit.

---

### Post by pmlxuser on 2009-08-19
> **mcduck said:**
> wouldn't that actually ask for password after the job has finished? THe "sudo" isn't execueted before that.. ;)

A trick to solve the problem, while still running the actual job as normal user, would be to use sudo's ability to run things as any user, not just root:

```
#! /bin/sh
sudo -u cholericfun job 
halt
```

Now run the script with "sudo ./yourscript", and type your password. It will start the job as the user specified,  and when done run the shutdown command which won't require password any more (you already gave it when you started the script)

Thanks man this should really do the trick. 
I am just learning this scripting thing
however 
```

$ /sbin/shutdown -h now

```
does not need a sudo password to execute.

---

### Post by mcduck on 2009-08-19
> **pmlxuser said:**
> Thanks man this should really do the trick. 
I am just learning this scripting thing
however 
```

$ /sbin/shutdown -h now

```
does not need a sudo password to execute.

It should require, unless you have changed something.
```

$ shutdown -h now
shutdown: Need to be root
$
```

Shutdown through GDM is another thing, *that* doesn't require root permission.

---

### Post by cholericfun on 2009-08-19
Ok,
thats odd,

when in su mode, my program doesnt work because it cant find some shared libraries...  (really dont get that behaviour)

also i didnt get the ```
sudo -u me ./job
``` to run,
when i ```
sudo ./jobscript
``` then it just complains that it doesnt have a passwrd for "me". 

sorry for beeing a bit slow here, i'm not aquaintet with the shell as much.

EDIT

ok, actually a typo in the script...

however i get the same error as with running the whole thing as root: the job cant find some shared libraries.
how is that???


maybe i could change the permissions of shutdown?
(how do i do that)
thanks

---

### Post by Penguin Guy on 2009-08-19
```
#!/bin/bash
# Script #

do_Job1
do_Job2
shutdown -h now
exit $?
```

$ sudo Script

---

### Post by cholericfun on 2009-08-19
ok,

i did a very insecure alternative that i'm not going to elaborate here...

any better ideas from anyone?

re Penguin_guy

no luck for me, still a problem with shared libs

./roms: error while loading shared libraries: libguide.so: cannot open shared object file: No such file or directory

---

### Post by mcduck on 2009-08-19
> **cholericfun said:**
> Ok,
thats odd,

when in su mode, my program doesnt work because it cant find some shared libraries...  (really dont get that behaviour)

also i didnt get the ```
sudo -u me ./job
``` to run,
when i ```
sudo ./jobscript
``` then it just complains that it doesnt have a passwrd for "me". 

sorry for beeing a bit slow here, i'm not aquaintet with the shell as much.

EDIT

ok, actually a typo in the script...

however i get the same error as with running the whole thing as root: the job cant find some shared libraries.
how is that???


maybe i could change the permissions of shutdown?
(how do i do that)
thanks

I didn't mean running the script with "sudo -u". But running the commands *inside* the script with "sudo -u", to run them as your normal user.

The script itself should be ran normally with sudo, without specifying a user, to make it run as root.

```
#!/bin/sh

sudo -u yourusername some_command
sudo -u yourusername some_other_command
halt
```
and the run the scriupt with sudo, without the "-u username"-part.

```
sudo /path/to/yourscript.sh
```

Now the script runs as root, executes the commands as your user, and then shuts down the machine.

edit: I just tested this, and it works fine. If you have problems getting it to work it's most likely related to the actual job you are trying to do, so  can't help with it without knowing more about it.. But make sure to use full paths for everything you do, just to make sure tha you'r issues are not caused by some things being in one user's path but not in root's path.

---

### Post by cholericfun on 2009-08-19
re McDuck

sorry for not writing clearly - i did write sudo -u ... inside the script

will try it with full paths (what is the "root path"?) - sounds like it might actually work with that.

thanks

---

### Post by mcduck on 2009-08-19
root's path. As in the $PATH variable, which defines the directories the system looks up for programs when you run a command.

When you execute a command, say "ls" for example, the system checks the directories defined in the user's $PATH variable and tries to find executable file called "ls". If it fins one, it runs it, if nothing is found you get error that such command doesn't exist. This is what allows you to run commands from any directory simply by typing the name of the command.

So waht I meant with full paths is that instead of using locations like Desktop/somefile use full paths like /home/username/Desktop/somefile. IF this is relevant or not depends on the job you are trying to do before running the shutdown command. :)

---

### Post by cholericfun on 2009-08-19
Ok,
thanks for the explanation re path.

i'm running an ocean model, ROMS which unfortunatly makes use of a lot of other programs (netcdf, hdf5, et cet.) that i had to install which i'm sure are not in the roots path but i dont really have time now to go about finding them all and fixing this...


so i called ```
sudo visudo
```
and added
```
my_username ALL = NOPASSWD: /sbin/shutdown
```

now with 
```
sudo shutdown -hP 10
```
it doesnt ask for a passwrd anymore
(unless it was still saved... but i kind-of ruled that out)


i'm doing a 20 minute test run now

---

### Post by mister_p_1998 on 2009-08-19
I do a scheduled shutdown every weekday at 18:05, just setup a cron to do this when you are sure the big job has finished.

Sudo gedit /etc/crontab

enter the line: 15 0 * * *    root /sbin/shutdown -h 1

this shuts down the pc at 12:15am every day of every week of every month.

Steve

---

### Post by cholericfun on 2009-08-19
re: Mister_P_1998

well, thats what i wanted to avoid... guessing the time of the shutdown.
i could just type sudo shudown -hP +date&time but i felt like doing it more elegantly and not run into the danger of shuting down before the job was finished or trading off with a lot of idle computer time 

anyhow, my last solution worked, 
thanks for all the hints and tips!
this forum really makes linux a productive experience!

---

