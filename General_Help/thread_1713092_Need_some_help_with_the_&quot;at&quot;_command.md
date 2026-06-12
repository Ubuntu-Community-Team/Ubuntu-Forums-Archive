---
title: "Need some help with the &quot;at&quot; command"
date: 2011-03-23
forum: General Help
---

### Post by tbrammer on 2011-03-23
All,

I'm having issues scheduling commands with the *at* command.

I'm just looking for a one liner that will create a job from standard input. I've tried the following:

```
touch testfile | at now + 1 minute
```This ignores the at command completely and just touches the file. This is also true if the two commands are inverted, though both ways indicated a job has been created...

```
at now + 1 minute < /bin/touch test file
```This produces the following error:

```
syntax error. Last token seen: /
Garbled time
```Can anyone give me any insight on how to properly use this command? I'm just trying to drop run a script who's commands actually execute at a given time.

Thanks in advance,
-Tim

---

### Post by idoitprone on 2011-03-23
Did you ever consider the command sleep, if you only need a command as a timer?

I cannot take credit for this code, I learned the ; character as a command separator from someone else. 

```
sleep 1m; touch testfile
```btw the > is meant as a redirect output, error
The < is meant to redirect input
the pipe | is meant to pass data through a filter like sort
ex. ```
cat file | sort
```

---

### Post by Cheesehead on 2011-03-23
If you're typing on the command line (not from a script):

```
$ at now + 1 min
warning: commands will be executed using /bin/sh
at> touch testfile
```

I don't believe 'at' takes command-line arguments. It takes **job files** instead:

So create a job file, which is simply a list of shell commands:

```

# This is the jobfile. It's name is 'testjob'
touch testfile

```

Then set up your at job,

```
$ at -f testjob now + 1 min
```

And that should work for you (it works for me).
Scripting an 'at' job simply means the implied task of creating the jobfile(s)

---

### Post by gordintoronto on 2011-03-23
"touch testfile | at now + 1 minute"

You have said, "touch testfile, and send the output to "at." Of course, it happens right now.

---

### Post by tbrammer on 2011-03-28
Thanks everyone for the help. These command work from command line, but when trying to script the creation of this job, I'm having no luck. Perhaps it would help to give a bit more detail about the scenario.

I'm attempting to update 200 ubuntu machines, but don't want the update to actually run until late at night when the machine isn't in use. Each box already has a cron based auto update running that I plan to take advantage of. What this means though, is that I have to pull the file, schedule it, and run it all from scripts...

Is using "at" just the wrong solution for this? Should I just try doing a one off cron job instead?

---

### Post by gordintoronto on 2011-03-28
Can't you just change the time that the auto-update runs?

---

### Post by tbrammer on 2011-03-29
```
at -f testjob now + 1 min
```

This worked for me. Thanks very much Cheesehead. I appreciate it.

---

