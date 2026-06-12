---
title: "&quot;at&quot; scheduler not working"
date: 2010-07-28
forum: General Help
---

### Post by Volt9000 on 2010-07-28
I recently read about "at" and thought it was neat, so I wanted to try it out. Unfortunately, it doesn't seem to do what it's supposed to.

I would type:

at now + 1 min

Then in the prompt I would type:

echo hello
zenity --info --text="HELLO"
<Ctrl+D>

I confirm the job is entered with "atq" and sure enough, the job is there, for the correct time. When the time comes around, nothing happens, and the job disappears. I don't see any text in the console, nor do I see a zenity infobox pop up.

Am I doing something wrong?

---

### Post by chopinhauer on 2010-07-28
> **Volt9000 said:**
> Am I doing something wrong?     

**at** retains all environment variables set at the time of the scheduling, except DISPLAY, TERM and _. Therefore 'zenity' doesn't know which X server to connect to. Try  exporting the DISPLAY variable with:
```

export DISPLAY=:0.0
zenity --info --text="Hello world!"

```

**Edit:** Normally the output of the commands is sent you by mail. That is if you have a mail server running on the box or at least something that emulates sendmail.

---

### Post by AlphaLexman on 2010-07-28
I just tried your commands and got this error:
```
warning: commands will be executed using /bin/sh
```
even though I am in a bash shell.

Any ideas?

---

### Post by chopinhauer on 2010-07-28
> **AlphaLexman said:**
> 
Any ideas?


It is just a way to warn you that the shell that will execute the commands is not your usual shell. So no configuration files will be read whatsoever. And no **bashisms** are allowed.

---

### Post by Volt9000 on 2010-07-28
> **chopinhauer said:**
> **at** retains all environment variables set at the time of the scheduling, except DISPLAY, TERM and _. Therefore 'zenity' doesn't know which X server to connect to. Try  exporting the DISPLAY variable with:
```

export DISPLAY=:0.0
zenity --info --text="Hello world!"

```

**Edit:** Normally the output of the commands is sent you by mail. That is if you have a mail server running on the box or at least something that emulates sendmail.

Alright, that worked, thanks (with zenity anyways.)
But what if I want the output of echo displayed to the terminal? I don't have a mail server set up on this machine. Would I have to set up a cronjob?

---

### Post by chopinhauer on 2010-07-28
> **Volt9000 said:**
> 
But what if I want the output of echo displayed to the terminal? I don't have a mail server set up on this machine. Would I have to set up a cronjob?


You must specify the name of the terminal and redirect all output to this terminal. For example:
```

piotr@luthien:~$ TTY=`tty` at now + 1 min
warning: commands will be executed using /bin/sh
at> echo "Hello world!" >$TTY 2>&1
at> <EOT>

```
The **tty** command gives you the name of your terminal device.

---

### Post by ruehara on 2010-07-28
The usual use of "at" is to execute scripts or programmes.

If you created a script with your commands in, then gave the instruction (assuming your script is called 'testit.sh')

                   at now + 1 minute < testit.sh

It would execute the commands in your script.

---

### Post by Volt9000 on 2010-07-28
> **chopinhauer said:**
> You must specify the name of the terminal and redirect all output to this terminal. For example:
```

piotr@luthien:~$ TTY=`tty` at now + 1 min
warning: commands will be executed using /bin/sh
at> echo "Hello world!" >$TTY 2>&1
at> <EOT>

```
The **tty** command gives you the name of your terminal device.

Why do I have to set that TTY environment variable (if that's indeed what that is doing)? Doesn't the at program "know" what terminal I'm calling it from?

---

### Post by chopinhauer on 2010-07-28
> **Volt9000 said:**
> 
Doesn't the at program "know" what terminal I'm calling it from?


'at' jobs are not called by your terminal, but by the **atd** daemon. They usually don't care how did you schedule them and they will be executed whether you are logged in or not.

Unlike X clients, which need to connect to the server themselves, the console clients are already connected to the terminal, so the terminal device is not stored in any environment variable.

Defining an environment variable to store the terminal device is obviously not necessary and the name of the variable is not important.

Anyway 'at' jobs usually either don't output anything or store their results in files.

---

### Post by Volt9000 on 2010-07-29
Ok, I understand, thanks!

---

