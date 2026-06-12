---
title: "Howto: Shutdown on exit?"
date: 2010-02-28
forum: General Help
---

### Post by CraXyOW3 on 2010-02-28
I have googled alot and i can not find what i am looking for.
Also i am a stable *nix newbie still :/

What i want is either a script or a program that simply shutdown my computer if a process/program is closed.

i.e
startup, run enna, if enna is closed, shutdown computer.

As i think you already figured out is that this is a media pc.

Is bash scripts similar to windows bat files ?
They tend to run one command if scripted in newbstyle and when that first command is finished it runs the next one.

i.e
run notepad - runs notepad (then close it)
run firefox - runs firefox after notepad is closed.

if they work similar then could i use a script to run enna and another command like shutdown when enna exits.

Ty for future help ...

---

### Post by cjhabs on 2010-02-28
Shell scripts (like bat files) work the way you describe so long as you don't tell the commands to run in the background (with an &).
So:
#!/bin/sh
xterm
shutdown

will fire up an xterm window and when you quit that xterm window, it will run the shutdown command.
Replace xterm with the command of your choice.
Do "man shutdown" to find the appropriate options for shutting down the system the way you want.
If the command is not in your path, include the full path to the command. e.g.:
#!/bin/sh
/usr/bin/xterm
/sbin/shutdown

You may need to sudo the shutdown, depending upon your configuration.

---

### Post by CraXyOW3 on 2010-03-01
Thank you for showing me in the right directions!

Got it all working now and with a little bit more googling with the aid of info from you, i got this little script working just as i wanted.

mousepad enna.sh

containing:

#!/bin/sh
enna
shutdown -h now

Then a "chown root enna.sh"
then "chmod 4755 enna.sh"

Then put it onto startup. done.

Funny tho, needing help for such a simple thing, but hey.
Again, thnx!

---

### Post by richardsith on 2010-07-14
hi,
I need the same thing just one question how to make running the script on startup of ubuntu?
thanks a lot

---

### Post by WorMzy on 2010-07-14
The easiest way would be to create an entry for it in System -> Preferences -> Startup Applications, but I can't recommend this type of auto-shutdown script, it sounds like a great way of accidentally losing unsaved work to me. But still, if you want to use it, it's your choice.

---

### Post by beatdawookie on 2010-07-14
> **richardsith said:**
> hi,
I need the same thing just one question how to make running the script on startup of ubuntu?
thanks a lot
 
 
[http://ubuntuforums.org/showthread.php?t=370989](http://ubuntuforums.org/showthread.php?t=370989)

---

