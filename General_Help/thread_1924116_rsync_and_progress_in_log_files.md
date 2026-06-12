---
title: "rsync and progress in log files"
date: 2012-02-12
forum: General Help
---

### Post by diskmaster23 on 2012-02-12
I have setup a rsync cron job to sync some data from my server to my local box, but it is alot of data. Since all this is being done via cron jobs, the process runs in the background, but I would like to be able to track its progress.

How do I track the progress of this cron job while rsync syncs in the background?

EDIT
I have already implemented -v option and -P option, but it only shows when the file was completed in the log file. The -P option only shows up when you run it at the terminal, not as a cron job. I need a way to peering into the process itself if the -v -P isn't giving me up to the second information of the remaining bytes of the file(s) being transferred in the log file.

---

### Post by sleepyhollows on 2012-02-12
What a wonderfully liberal forum.

Certainly no Stack Exchange (from where I was banned, apparently just for wanting to get involved and help...)

Just search on the web for how to schedule rsync jobs on linux. You will likely want email notification as well.

Any solution will do, it's not specific to ubuntu.

And before getting narky that I did not actually answer, take a breath and appreciate my answer for it will likely have the magic effect of causing another to come along and go one step further and actually provide you the direct answer

---

### Post by papibe on 2012-02-12
A couple of ideas:
[LIST]
[*]use rsync with the verbose option, and redirect its output to a log that you can check.
[*]get your script inside a deattached virtual terminal (using the program 'screen'), so you can attached it any time you need to see what is going on.
[/LIST]
Hope it helps, and tell us if you need more details on those ideas.
Regards.

---

### Post by diskmaster23 on 2012-02-12
> **sleepyhollows said:**
> What a wonderfully liberal forum.

Certainly no Stack Exchange (from where I was banned, apparently just for wanting to get involved and help...)

Just search on the web for how to schedule rsync jobs on linux. You will likely want email notification as well.

Any solution will do, it's not specific to ubuntu.

And before getting narky that I did not actually answer, take a breath and appreciate my answer for it will likely have the magic effect of causing another to come along and go one step further and actually provide you the direct answer

I know how to do the log file, but it doesn't give me any progress information, which is why I am asking.

Perhaps getting progress information while it runs in the background from a log file is the wrong format, but I am trying to get myself in the right direction.

But thank you for your 'useful' comment.

---

### Post by diskmaster23 on 2012-02-12
> **papibe said:**
> A couple of ideas:
[LIST]
[*]use rsync with the verbose option, and redirect its output to a log that you can check.
[*]get your script inside a deattached virtual terminal (using the program 'screen'), so you can attached it any time you need to see what is going on.
[/LIST]
Hope it helps, and tell us if you need more details on those ideas.
Regards.

Hmm.....any tips on the deattached virtual terminal? Will that allow me to see the progress of the already executed cron job?

---

### Post by Lars Noodén on 2012-02-12
> **diskmaster23 said:**
> I know how to do the log file, but it doesn't give me any progress information, which is why I am asking.

You're not really going to be able to capture meaningful output from --progress.  What is missing that -v does not give you?

---

### Post by diskmaster23 on 2012-02-12
> **Lars Noodén said:**
> You're not really going to be able to capture meaningful output from --progress.  What is missing that -v does not give you?

The -v writes in the log when when a file is completed transferring, but I have no idea where the file is while it is transferring. I probably won't be watching the cron job all the time, but I would like to peek into the process and find out where it is in transferring the data; I am still not sure the log file is the right tool, probably isn't.

---

### Post by sleepyhollows on 2012-02-12
> **diskmaster23 said:**
> 

But thank you for your 'useful' comment.

Not a problem. Im glad it helped, as I said it would.

pabibe is on the money with screen

Or, check out these options: [http://www.debianadmin.com/rsync-backup-web-interfacefrontend-or-gui-tools.html](http://www.debianadmin.com/rsync-backup-web-interfacefrontend-or-gui-tools.html)

Their monitoring capabilities are probably not as in depth as you require.

In my experience, progress has only been useful when I was trying to understand rsync. 
When rsync crashes, the best clue has usually been what file it stopped on (or whether it actually got started on a file at all). 
-v will log the last file it was attempting. Usually the file it crashes on is a large file.

Best way to have rsync 'catchup' on it's self, given multiple failures, is to use --inplace, or --partial. This way, it eventually gets there.

Look at that, my own lack of effort has caused my own self to put in more effort.

---

### Post by Khayyam on 2012-02-12
diskmaster23 ..

its fairly simple ...

```
rsync -args --logfile=/home/logs/rsync.log source dest
```

The cronjob would need to be run under the user who can write to --logfile of course.

You could then view the file as and when you wanted to see what was happening

```
ssh user@host "tail -f  ~/logs/rsync.log"
```HTH ...

---

### Post by SeijiSensei on 2012-02-12
It sounds like you're looking for a "progress meter" or the like which would say you've moved 53% of the files or give the number of bytes transferred and remaining.  Rsync doesn't support this function as far as I know.

As others have said, if you use "-v" you'll get a list of files as they are sent that you can track with "tail -f /var/log/rsync" or wherever you direct the output.  The "--stats" parameter provides summary statistics but not a progress measure.

---

### Post by diskmaster23 on 2012-02-12
> **SeijiSensei said:**
> It sounds like you're looking for a "progress meter" or the like which would say you've moved 53% of the files or give the number of bytes transferred and remaining.  Rsync doesn't support this function as far as I know.

As others have said, if you use "-v" you'll get a list of files as they are sent that you can track with "tail -f /var/log/rsync" or wherever you direct the output.  The "--stats" parameter provides summary statistics but not a progress measure.

It has the -P option, but it only shows while you are running the command at a terminal, not as a cron job and into the log file.

---

### Post by Khayyam on 2012-02-12
> **SeijiSensei said:**
> It sounds like you're looking for a "progress meter" or the like which would say you've moved 53% of the files or give the number of bytes transferred and remaining.  Rsync doesn't support this function as far as I know.

Actually it does, '--progress', or the '-P' switch (I see now form the OP's edits that s/he was using '-P'). The problem is that because --progress is updating the screen there are control characters printed, so its not really designed for non-interactive shells (such as cron).

The output of --progress could be redirected to a file but then the file woud contain control characters and would need to be parsed with sed 's/\r/\n/g' to remove these chars. So, obviously thats not going to work with 'tail -f'. 

So, really, what the OP wants is an interactive feature for a non-interactive shell, and that is somwhat of an ask. The closest they will get, I think, is via '--log-file='.

best ... khay

---

### Post by diskmaster23 on 2012-02-12
> **Khayyam said:**
> Actually it does, '--progress', or the '-P' switch (I see now form the OP's edits that s/he was using '-P'). The problem is that because --progress is updating the screen there are control characters printed, so its not really designed for non-interactive shells (such as cron).

The output of --progress could be redirected to a file but then the file woud contain control characters and would need to be parsed with sed 's/\r/\n/g' to remove these chars. So, obviously thats not going to work with 'tail -f'. 

So, really, what the OP wants is an interactive feature for a non-interactive shell, and that is somwhat of an ask. The closest they will get, I think, is via '--log-file='.

best ... khay

<shrugs> I figured I was asking too much, but I am not as knowledgeable as some folks around here. So I thought I would ask.

Thanks for everyone's help.

---

### Post by papibe on 2012-02-12
> **diskmaster23 said:**
> Hmm.....any tips on the deattached virtual terminal? Will that allow me to see the progress of the already executed cron job?
It would allow you to connect to the terminal where the command it is actually being executed.

IMHO, this is very helpful when you are rsyncing a few big files, instead of several small to medium files. In this case the option --progress make more sense than -v. 

I personally use a combination of screen and rsync to share family photos and videos with my brother.

Inside cron you need to create a detached screen:
```
screen -dmS NameOfScreen your_rsync_script.sh
```
At any time you can check if there are screens actives by doing:
```
screen -ls
```
If you see something like this:
```
There is a screen on:
	3637.NameOfScreen	(02/12/2012 08:31:02 PM)	(Detached)
1 Socket in /var/run/screen/S-user.

```
it means that the script is still running inside the screen named 'NameOfScreen'. In order to attach (connect) to the virtual screen do this:
```
screen -r NameOfScreen
```
To leave things running as they were, de attach from the screen by pressing Ctrl+a d (control a, and then d).

Hope it helps.
Regards.

---

### Post by diskmaster23 on 2012-02-12
> **papibe said:**
> It would allow you to connect to the terminal where the command it is actually being executed.

IMHO, this is very helpful when you are rsyncing a few big files, instead of several small to medium files. In this case the option --progress make more sense than -v. 

I personally use a combination of screen and rsync to share family photos and videos with my brother.

Inside cron you need to create a detached screen:
```
screen -dmS NameOfScreen your_rsync_script.sh
```
At any time you can check if there are screens actives by doing:
```
screen -ls
```
If you see something like this:
```
There is a screen on:
	3637.NameOfScreen	(02/12/2012 08:31:02 PM)	(Detached)
1 Socket in /var/run/screen/S-user.

```
it means that the script is still running inside the screen named 'NameOfScreen'. In order to attach (connect) to the virtual screen do this:
```
screen -r NameOfScreen
```
To leave things running as they were, de attach from the screen by pressing Ctrl+a d (control a, and then d).

Hope it helps.
Regards.
I'll give it a try.

---

### Post by diskmaster23 on 2012-02-13
> **papibe said:**
> It would allow you to connect to the terminal where the command it is actually being executed.

IMHO, this is very helpful when you are rsyncing a few big files, instead of several small to medium files. In this case the option --progress make more sense than -v. 

I personally use a combination of screen and rsync to share family photos and videos with my brother.

Inside cron you need to create a detached screen:
```
screen -dmS NameOfScreen your_rsync_script.sh
```
At any time you can check if there are screens actives by doing:
```
screen -ls
```
If you see something like this:
```
There is a screen on:
	3637.NameOfScreen	(02/12/2012 08:31:02 PM)	(Detached)
1 Socket in /var/run/screen/S-user.

```
it means that the script is still running inside the screen named 'NameOfScreen'. In order to attach (connect) to the virtual screen do this:
```
screen -r NameOfScreen
```
To leave things running as they were, de attach from the screen by pressing Ctrl+a d (control a, and then d).

Hope it helps.
Regards.

The script looks like this
```

#!/bin/bash
cmd="rsync -avzhP --verbose --log-file=/data/server-rsync-log --owner=david --group=admin --chmod=a+rw,g+rw,g+rw,o-wx /data/server-remote/ /data/server-local/"
eval $cmd # execute command

```

The problem is, when I run ```
screen -dmS rsync -avzhP --verbose --log-file=/data/server-rsync-log --owner=david --group=admin --chmod=a+rw,g+rw,g+rw,o-wx /data/server-remote/ /data/server-local/
```
I get this ```
Screen version 4.00.03jw4 (FAU) 2-May-06
```

So I thought I had to run it like this ```
screen -dmS /usr/bin/ssh-server-rsync
``` but when I do, I get this ```
Must run suid root for multiuser support.
```

What am I doing wrong?

---

### Post by papibe on 2012-02-13
screen expects a name after the -S option, and then a command. Try this:
```
screen -dmS **myscreen** rsync -avzhP --verbose --log-file=/data/server-rsync-log --owner=david --group=admin --chmod=a+rw,g+rw,g+rw,o-wx /data/server-remote/ /data/server-local/
```
Although, I would rather run it like this:
```
screen -dmS myscreen /path/to/myrsync,sh
```
where myrsync.sh contains the rsync command:
```
#!/bin/bash
rsync -avzhP --verbose --log-file=/data/server-rsync-log --owner=david --group=admin --chmod=a+rw,g+rw,g+rw,o-wx /data/server-remote/ /data/server-local/
```
Let us know how it goes.
Regards.

---

### Post by diskmaster23 on 2012-02-16
> **papibe said:**
> screen expects a name after the -S option, and then a command. Try this:
```
screen -dmS **myscreen** rsync -avzhP --verbose --log-file=/data/server-rsync-log --owner=david --group=admin --chmod=a+rw,g+rw,g+rw,o-wx /data/server-remote/ /data/server-local/
```
Although, I would rather run it like this:
```
screen -dmS myscreen /path/to/myrsync,sh
```
where myrsync.sh contains the rsync command:
```
#!/bin/bash
rsync -avzhP --verbose --log-file=/data/server-rsync-log --owner=david --group=admin --chmod=a+rw,g+rw,g+rw,o-wx /data/server-remote/ /data/server-local/
```
Let us know how it goes.
Regards.

I just wanted to let everyone know that it worked. Consider this thread solved.

---

