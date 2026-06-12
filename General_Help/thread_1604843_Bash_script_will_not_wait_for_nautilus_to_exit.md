---
title: "Bash script will not wait for nautilus to exit"
date: 2010-10-24
forum: General Help
---

### Post by FatalKeystroke on 2010-10-24
I'm having trouble with a bash script.
Does anyone know why this doesn't work?
```
nautilus ./ &
wait $!
```I'm writing a script which will extract a series of .rar files, present the extracted files to the user in nautilus so they may modify them, then when the user closes nautilus, the modified files are packed back into the archive.

---

### Post by FatalKeystroke on 2010-10-27
I hate to do two consecutive posts, but I need to get this script working soon and I haven't found another way yet.

---

### Post by VCoolio on 2010-10-27
Use && so the script waits for the first command to finish successfully, instead of just & which will execute the second while the first is still running. Use command 1 || command 2   to execute 2 if 1 fails.

---

### Post by FatalKeystroke on 2010-10-27
I don't understand, do you mean
```
nautilus ./ && wait $!
```
Because that doesn't work.

Am I misunderstanding your post?

---

### Post by VCoolio on 2010-10-27
> **FatalKeystroke said:**
> I don't understand, do you mean
```
nautilus ./ && wait $!
```
Because that doesn't work.

Am I misunderstanding your post?

No, that's what I meant, but I'm not sure what you want with the 'wait $!' part. Why not just something like 'nautilus /extracted/folder && tar /extracted/folder'? Or maybe nautilus is difficult because it already sort of runs drawing your desktop and stuff. Let the script spawn two windows: one nautilus to make modifications, and one zenity --info --text="Click here when done". Let the script wait for the zenity window to be closed, then continue.

---

### Post by StephenDavison on 2010-10-27
I think your problem is the 'nautilus' command is not doing what you think it is.  On my out-of-the-box Ubuntu install, nautilus is running as a child process of gnome-session, and is managing the desktop.  Subsequent executions nautilus from a shell (prompt or script) trigger the already running process to open a new browser window without continuing to run a new process in the foreground.  Consequently, it doesn't matter what you do in your shell script -- your nautilus command is going to exit almost immediately.  I have no idea how you would go about getting another nautilus process running that you can wait on.

---

### Post by VCoolio on 2010-10-27
> **StephenDavison said:**
> I think your problem is the 'nautilus' command is not doing what you think it is.  On my out-of-the-box Ubuntu install, nautilus is running as a child process of gnome-session, and is managing the desktop.  Subsequent executions nautilus from a shell (prompt or script) trigger the already running process to open a new browser window without continuing to run a new process in the foreground.  Consequently, it doesn't matter what you do in your shell script -- your nautilus command is going to exit almost immediately.  I have no idea how you would go about getting another nautilus process running that you can wait on.

Now that I think about it I get the problem a little better. The $! is closer to a solution than I thought (a new nautilus window has a new pid, right?). Just not sure if the wait command is appropriate. I don't know how scripts and commands in scripts handle shells. Try [this link](http://www.odi.ch/weblog/posting.php?posting=291).

---

### Post by StephenDavison on 2010-10-27
No, the new nautilus window does not have a new pid.  Try this sequence of commands in a terminal window:

ps -ef |grep nautilus
nautilus
ps -ef |grep nautilus

Both ps commands should show the same PID and PPID even though a new nautilus browser window is open.  The PPID will be for gnome-session (assuming a vanilla Ubuntu install using GNOME).

---

### Post by efflandt on 2010-10-27
I think Stephen is on the right track.

This works (waits):

```
#!/bin/bash
coproc xterm
echo coproc PID $COPROC_PID
wait $COPROC_PID
echo finished
```Following does not wait. Says finished even though nautilus is still up (but the process that launched another instance has disappeared):

```
#!/bin/bash
ps aux | grep nautilus
coproc nautilus ./
echo coproc PID $COPROC_PID
ps aux | grep nautilus
wait $COPROC_PID
echo finished
ps aux | grep nautilus
```

---

### Post by FatalKeystroke on 2010-10-27
> **efflandt said:**
> I think Stephen is on the right track.

This works (waits):

```
#!/bin/bash
coproc xterm
echo coproc PID $COPROC_PID
wait $COPROC_PID
echo finished
```
This may wait for xterm, but it doesn't work for nautilus. 

The explanation given by StephenDavison seems to be right and I looked for a way to create a separate nautilus process but had no luck. I could use a different file manager if necessary, but it must be able to preview jpeg images in the browsing pane. If anyone knows of one that does this I could use that instead, but I would still prefer to use nautilus if I could help it.

I thought of perhaps using zenity to create a window that the user can click when they're done editing the files and have the script wait for that to return, but again, I'd rather not do that if I can help it. I'll use that as a last resort if I have to.

---

### Post by FatalKeystroke on 2010-11-05
Ok, so I ended up using Zenity to block the script. It works well even if not how I intended.

Thanks for everyones help.

---

