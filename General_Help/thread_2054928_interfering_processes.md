---
title: "interfering processes"
date: 2012-09-08
forum: General Help
---

### Post by twipley on 2012-09-08
I am running an application which is *very* timing sensitive, and which has to be ran for quite a time just for precise [average] values to be determined.

But, as I am aware of, there are interfering processes here and there in the background, which jobs are to enrich the experience of the user -- such as update notifications (happens once a day), backup-management reminders (happens once in a while), and screen-locking automatisms (default is set to 10 minutes).

The question I am asking is, is there any practical way to "stop time," so as to speak, and make every such processes go to sleep? gnome-system-monitor reports CPU-usage fluctuations due to various factors. There is also Compiz for which the monitor seems to report background activities.

Would there be a viable way for any such interfering process to be terminated? Ubuntu is really the OS of choice, and one would be sad moving to another distro as a solution -- as the real solution is to be located *within* the Ubuntu realm -- especially because one is such a Linux layman. In short, any solution piece, however strange, is more than welcomed, and I hope more than one can benefit from such a thread.

---

### Post by Epodx64 on 2012-09-08
Does your program have to run from a GUI? if not switch over to TTY1 ( ctrl+alt+f1 ) login to the console then type

ps -A | grep gdm

get the pid number xxxx 

then

sudo kill -9 pid

that should stop X and everything running from TTY7 then if it's possible just run your program from the TTY1 Console unless of course it's a GUI program then you could disable the services from gnome-startup-manager or something like that

---

### Post by The Cog on 2012-09-08
As Epodx64 says, our best bet (if possible) is to kill off the GUI and run from a tty console. 

In recent versions of Ubuntu the desktop manager is lightdm rather than gdm, and the command **sudo service lightdm stop** should stop it and drop you to a tty console.

Also, you can run a task at a higher priority by running it with a reduced "niceness". This will give it more priority over CPU usage than other tasks, but it won't completely lock out other tasks, and may still be subject to pauses waiting for occasional disk I/O.

---

### Post by twipley on 2012-09-08
Thanks for the answers.

Unfortunately, the program seems to require a GUI to run, and segfaults if ran without lightdm or such.

One might have more success trying the pointed-to way of managing startup elements, though "session and startup," available from the software centre, and tweaking from the "application autostart" tab.

Then, the included "power statistics" application can display relevant info about processor-wakeup calls, which may be useful for diagnosis.

On the whole, I believe this is a viable approach. If nobody else tries to disable every item listed on that tab before I do, I might try on quantal and report back, hopefully from the same computer if I am able to revert changes thereafter.

---

### Post by twipley on 2012-09-08
It has happened to me that the "session and startup" application I had downloaded is designed to work with the Xfce desktop environment. Therefore, the solution might lie in using Xubuntu or Lubuntu instead of Ubuntu.

For example, Lubuntu is quite lightweight and I have read one can manage startup element and monitor resources through the following: bum & lxtask;

This looks as a viable approach to going real light. :)

---

### Post by MadCow108 on 2012-09-08
depending on the required precision you have to install a realtime kernel for this task:
[http://en.wikipedia.org/wiki/Real-time_operating_system](http://en.wikipedia.org/wiki/Real-time_operating_system)

the default kernel shipped with ubuntu is not suitable for such a task as its scheduling methods and other stuff it does is non-deterministic and depends on the current state of the machine.

the linux realtime patches are here:
[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/)

---

### Post by twipley on 2012-09-08
> **MadCow108 said:**
> for such a task you have to install a realtime kernel
[http://en.wikipedia.org/wiki/Real-time_operating_system](http://en.wikipedia.org/wiki/Real-time_operating_system)

the default kernel shipped with ubuntu is not suitable for such a task as its scheduling methods and other stuff it does is non-deterministic and depends on the current state of the machine.
that's nice info.

edit: (lubuntu might be tried.) -- as it seems best suited for the task at hand;

---

### Post by twipley on 2012-09-14
> **twipley said:**
> there are interfering processes here and there in the background, which jobs are to enrich the experience of the user -- such as update notifications (happens once a day), backup-management reminders (happens once in a while), and screen-locking automatisms (default is set to 10 minutes).

found the solution to disabling interfering processes -- marking thread as solved:

> **kgarbutt said:**
> Cut & paste this into the terminal:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

After this, then reopen 'Startup Applications' and all will be good.

---

