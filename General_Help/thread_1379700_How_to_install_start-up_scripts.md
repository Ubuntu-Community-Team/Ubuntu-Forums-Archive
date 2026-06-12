---
title: "How to install start-up scripts"
date: 2010-01-12
forum: General Help
---

### Post by dyslexia on 2010-01-12
I need to install two bash scripts at two different points in boot process:

one script needs to be run right after boot, but just before the login screen (gdm, I presume) starts.

another needs to be run every time X starts, at the end of the start process (right after login screen is displayed, right after user X session is initiated.)

the problem is that I can't find the scripts to hack to insert my bit of code...  it seems "xinitrc"s and "xsessions" are sourced all over the place, but when diagnostic messages are placed in the .d directories (and in the scripts themselves even) it appears that most (all even) of those scripts aren't even getting executed.

I do have one message comming in from /etc/rc.local that it did execute the file once at runlevel 2, ("N 2" which is the level it thinks it's at now).

So maybe I have my first script location?  Is GDM running at this point (when rc.local is sourced?)

xinit is twisty little maze of twisty passages,
HELP!

---

### Post by loboc on 2010-01-12
you can play with /etc/init.d/gdm in both the start and restart sections

---

### Post by john newbuntu on 2010-01-12
I am not sure on the dependencies on devices that you need in your script, but since processes are started asynchronously in an upstart system and in an event based manner, theoretically, you will need to add a job in /etc/init that emits an event, which then is used by gdm to run.  In the same way, you can execute your second job after you get the event "starting-dm" from gdm.conf job.

You can see several examples of jobs in /etc/init.  Please backup your system before doing any changes and wait for a second opinion for a possibly better idea.

---

### Post by Leppie on 2010-01-13
> **john newbuntu said:**
> you will need to add a job in /etc/init that emits an event, which then is used by gdm to run.
+1, the /etc/init folder is the place to put startup scripts to be sourced by upstart.
if you want to put extra commands in the gdm.conf script, you have to put these after the "script" label and before the "end script" label

---

### Post by dyslexia on 2010-01-13
Poking around /etc/init a little bit ... doesn't look like gdm.conf is that useful, because I need the display manaager running already.

there is a script called " /etc/gdm/PostSession/Default" which looks promising... (as did all the xsession stubs)... I will try that.

For one of the tasks, my script would needs to execute a command that would act on the user-session X server .. as if it were typed in the terminal   ( wacom module needs to be sent a xsetwacom command)

any ideas on how I "authorize" a process running as root to send messages via the display?

---

