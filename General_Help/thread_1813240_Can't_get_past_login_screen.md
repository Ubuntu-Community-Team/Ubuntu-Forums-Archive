---
title: "Can't get past login screen"
date: 2011-07-27
forum: General Help
---

### Post by Artorius89 on 2011-07-27
Hello!

**I'm unable to enter my account.** After I enter my password, Ubuntu briefly shows that black screen with white text (terminal style) telling you what it's doing and then it goes back to the login screen.
I've tried all kinds of sessions (except for the one called "User defined session"), including *safe mode*, but it doesn't help. The only thing working are the consoles you can summon by Ctrl+Alt+F1/2/3/...
If, in one of those consoles, I type (as suggested in similar threads) *startx*, it answers "Fatal server error: Server is already active for display 0". The command to reconfigure/reinstall the xserver doesn't help either.

I'm aware that this problem has already come up before, and I have tried following the instructions in similar threads but I haven't been able to solve the problem.

I'm running Ubuntu 11.04 on an Asus A6J laptop. Several days ago I installed the Edubuntu desktop package on top of Ubuntu, so perhaps I should say I'm running Edubuntu...

This is a big problem, so I hope somebody can help me.

---

### Post by linuxuser12345 on 2011-07-27
Log in using Classic mode. I had a similar problem, and once I started using classic, everything works fine!

Good luck :)

---

### Post by Artorius89 on 2011-07-27
Actually, I already usually log in in classic mode. Neither that nor safe mode helps.
But thank you for your interest.

---

### Post by linuxuser12345 on 2011-07-27
I would recommend switching to Ubuntu 10.10 or 10.04.3. Chances are, you probably won't run into this problem in either of those versions.

---

### Post by Artorius89 on 2011-07-27
But wouldn't that be equivalent to reinstalling 11.04? I would rather not do it, as I would lose new data since the last backup.
I've been using 11.04 since it came out and I've never had any similar problem, so I'm hoping that this could be more easily solvable than downgrading or reinstalling. Something must have gone wrong in my last session.

---

### Post by Wayne_V on 2011-07-27
ctrl-alt-F1, log in and run "tail -f /var/log/{dmesg,messages,*log} | tee ~/Xerror.log

ctrl-alt-F7 and try to log in at the GUI again

then go back to ctrl-alt-F1, hit ctrl-C and post Xerror.log

---

### Post by Artorius89 on 2011-07-27
Thank you.
Could you please suggest me a way of copying here that log? I have no idea, as I'm using this forum through another computer at my home (I obviously can't use mine, since I can't log into the GUI). Would there be any way of doing that through the console?
(Besides, is it a problem if I take away the tilde from the last part of your command? My keyboard layout (Italian) doesn't have it. [I changed the keyboard layout to US in the login screen, but that doesn't change anything in the console]).

---

### Post by Wayne_V on 2011-07-27
the ~ just means go to your home directory, so yeah, leave it off if it's a problem.

to post .... hmm ... can you email it to yourself?

$ cat Xerror.log | mail -s Xerror [email]you@somewhere.org[/email]

or do you have access to any ftp servers?  maybe someone knows of a public one?

---

### Post by Artorius89 on 2011-07-27
Unfortunately, the command you suggested to send the log to myself doesn't work:

> cat: Xerror.log: Non-existent file or directory
Null message body; hope that's ok
Please install an MTA on this system if you want to use sendmail!
Can't send mail: sendmail process failed with error code 255This is starting to look sad...

---

### Post by Wayne_V on 2011-07-28
yeah, that was a long shot thinking you might have sendmail set up ...

are you in the same directory you were when you ran "tail -f /var/log/{dmesg,messages,*log} | tee ~/Xerror.log"?

Did you leave off just the ~ or the ~/  ? Xerror.log is in / if you left of just the ~.

Do you have another computer you can use (assuming so since you are posting).   Try this:

On the bad computer:

sudo apt-get install openssh-server

On the good computer:

If it is windows, download pscp.exe from [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Then, in a command window, run "pscp.exe <user>@<linux box>:/Xerror.log ."
(if the second system is linux just replace pscp.exe with scp)

Now you should have Xerror.log in the current directory of the second system.

---

### Post by Artorius89 on 2011-07-28
Good day to you! Thanks a lot for keeping on helping me: I'm clueless and locked out of my laptop (not to mention unexperienced with the terminal).

> **Wayne_V said:**
> are you in the same directory you were when you ran "tail -f /var/log/{dmesg,messages,*log} | tee ~/Xerror.log"?

Did you leave off just the ~ or the ~/  ? Xerror.log is in / if you left of just the ~.
No, I didn't change directory. I had left off just the tilde, but now not even that, as I've found a way of typing it.

> **Wayne_V said:**
> yeah, that was a long shot thinking you might have sendmail set up ...
In a desperate attempt, I typed "sudo apt-get install sendmail" and then repeated your procedure: no error messages this time, but no mail in my inbox either.

> **Wayne_V said:**
> Then, in a command window, run "pscp.exe <user>@<linux box>:/Xerror.log ."
(if the second system is linux just replace pscp.exe with scp)
I have a PC running lubuntu (the one I'm using right now). I've tried your new suggestion, but it didn't work out, unfortunately: the good machine answered "cp: executing the stat of "<myname>@<mylaptop>" is impossible: no such file or directory.

If this doesn't work, could I copy the log to a USB device? How can I do that, please?

---

### Post by Wayne_V on 2011-07-28
did you use "cp" or "scp" ?  cp won't work ....

If it gives an error about not finding <mylaptop> you may need to use the IP address instead of the name (from 'ifconfig -a').

---

### Post by Artorius89 on 2011-07-28
I did use *scp*, although I just noticed I had inserted a space where it wasn't supposed to be. So I tried again (both with the user name and the IP address): instead of an error message, this time I got three lines explaining the usage of the scp command ("usage: scp [...]").

I wouldn't want you to feel like you're wasting your time. Perhaps I should investigate how to backup everything from the terminal and reinstall the system. I hope that would be easy.

---

### Post by Wayne_V on 2011-07-28
what was the exact scp command you used?   if it gave you a usage message you might have an extra space, forgot a space, or maybe left off the "   .   " on the end (which is shortcut just telling scp to copy the remote file to the current directory)

---

### Post by Artorius89 on 2011-07-28
You're right: I had left off the dot; I hadn't even noticed it was part of the command.
So I repeated the procedure correctly, trying all the IP addresses *ifconfig* provided, but even then it didn't work: one of them answered "connection refused", while the rest gave back "network unreachable".
Then, noticing that the Ubuntu live CD has an option to reinstall ("upgrade") the OS, leaving all my files intact, I tried that: what a mistake! The process encountered an error shortly after the beginning, and now Ubuntu won't start at all.
Well, now I'll follow the tutorials to recover my encrypted data via the live CD, and then reinstall the OS.

Thank you very much for your kind support. Unfortunately, I haven't been experienced enough to make your suggestions work.
Have a good summer! Auf Wiederschreiben, auf Wiederlesen!

---

