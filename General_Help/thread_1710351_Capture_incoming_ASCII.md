---
title: "Capture incoming ASCII"
date: 2011-03-19
forum: General Help
---

### Post by Don DeGregori on 2011-03-19
I want to capture text and save it to a file. It's coming in on /dev/USB0,at 56700 bps, 8N1. I need a short bash script to do this for about 10 seconds and then close the script. Then I want to look at the saved file. I'll go from there. Thanks.
Don

---

### Post by gzarkadas on 2011-03-19
You can use this chain of commands from within the terminal. If you want to make it a script, just put the line in a file and prepend a `#!/bin/bash' line at the start, then chmod the file to be executable. But it is better to just make this command an alias (type `help alias' inside a terminal for details) or a function inside your ~/.bashrc.

```

< /dev/USB0 cat > [your-file] & JOBPID=$! ; sleep 10 ; kill -s TERM $JOBPID

```Replace [your-file] with the desired path to the output file. When the command ends, open the file with `less' or any other viewer/editor to see the data.

What is done by the - serially executing due to ; - chain of (three) commands:

1. `cat' reads from the device and outputs to [your-file] as a background job (hence the &) while its pid (process id) is stored in the JOBPID variable (with the $! special parameter). Since it is a background job, the shell returns immediately and proceeds with the second command of the chain.

2. `sleep 10' makes the shell wait for 10 seconds (the time you specified); then it returns and the shell proceeds with the third command.

3. `kill ...' sends the terminate signal to the background job identified by JOBPID (ie your job), causing it to terminate orderly.

---

### Post by Hedgehog1 on 2011-03-19
gzarkadas,

Thanks for explaining what each portion of the command does.  I appreciate your extra effort on this.  Help us all learn new stuff!

***The More-Educated-Than-Five-Minutes-Ago Hedge***

:KS

---

### Post by Don DeGregori on 2011-03-20
gzarkadas,

I surely agree with the other gentleman! It's great to have some help which you have provided. I was tying to use minicom and runscript with little success. I could get it to open minicom and kill after a few seconds, but could not capture to a file at the same time. I'll try what you show.
Thanks, Don

---

### Post by Don DeGregori on 2011-03-20
Hi gzarkadas,

Your script snippet works fine as root, either sending as one liner on the terminal, or as a script.

But I'm having 1 heck of a time getting root to let go of /dev/USB0.
I can't execute it at all in the rest of the program as user. I can use sudo on the terminal. Don't think I can use sudo in a script. I've used chmod everywhere and tried to add user name to group. This works, but still same problem.

The serial device is an ACM type. The hardware is a serial/USB connecting to a Microchip MCP2200. The Linux procedure is this; 
lsmod | grep cdc...Get good result
I see it on /dev/tty/ACM0...Good result
Then do a ln -sf /dev/ttyACM0 /dev/USB0...Good result
Then do a stty -F /dev/USB0 57600...Good result
I see data on a file called baro.
Just can't run from user

Don

---

### Post by gzarkadas on 2011-03-22
The only reasons for not being able to run this as a normal user would be to either not have read rights on the device or not have a bash shell. Post the result of `ls -la /dev/tty/ACM0' as well as `</etc/group grep [your-user]' here to see what's going on. Also execute `</etc/passwd grep [your-user]' (_without_ posting the result here) and look at the end of the line to verify that you use bash and not sh or dash or whatever.

Btw, you can use sudo in a script (or gksudo if you don't want a console window to appear and prefer a gui dialog box), you 'll just have to provide your password at the point of sudo invocation.

---

