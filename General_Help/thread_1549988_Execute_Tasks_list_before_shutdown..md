---
title: "Execute Tasks list before shutdown."
date: 2010-08-10
forum: General Help
---

### Post by knax on 2010-08-10
When I shut down my computer I want to show some pending tasks that I have to do before leaving the office... 

I did a local application to manage those tasks, so basically I just want to run a command, and shut down after I kill the app executed.

I have already tried with these options:

* /etc/gdm/PostSession/Default --> this works only when I select LogOut option instead Shutdown.

* /etc/rc0.d/K01mycustomscript --> execute script after X  is killed

* $HOME/.bash_logout --> This looks like does nothing.

* ./app-to-run && sudo shutdown -h now --> Don't like it for 2 reasons, prompts for sudo password, and can't use my laptop shutdown button.

How could I modify Shutdown dialog ? should I recompile Gnome ?
Options?

I am using Ubuntu 10.04

---

### Post by sh3rif on 2010-08-13
Same problem here
I would like to save all my virlualbox vms before shutdown Im using 9.10
Thanks :)

---

### Post by hasi42 on 2010-08-26
> **knax said:**
> When I shut down my computer I want to show some pending tasks that I have to do before leaving the office... 

I did a local application to manage those tasks, so basically I just want to run a command, and shut down after I kill the app executed.

I have already tried with these options:

* /etc/gdm/PostSession/Default --> this works only when I select LogOut option instead Shutdown.

* /etc/rc0.d/K01mycustomscript --> execute script after X  is killed

* $HOME/.bash_logout --> This looks like does nothing.

* ./app-to-run && sudo shutdown -h now --> Don't like it for 2 reasons, prompts for sudo password, and can't use my laptop shutdown button.

How could I modify Shutdown dialog ? should I recompile Gnome ?
Options?

I am using Ubuntu 10.04

I'm having a similar problem (I want to avoid shutdown under certain circumstances) and my current "solution" looks as follows:
I removed the shutdown button from Gnome panel and added an application starter that executes a script which, after doing some stuff, does

[FONT=Fixedsys]gnome-session-save --shutdown-dialog[/FONT]

To do similar things from the login screen I had to use KDM instead of GDM.
KDM has in /etc/kde4/kdmrc the options HaltCmd and RebootCmd where I specified wrappers around /sbin/shutdown.

I'm afraid this doesn't help you with the shutdown button of your laptop.

Maybe it is more appropriate for you to call your app-to-run just before executing halt in /etc/init.d/halt (but this won't help you if your app-to-run needs X).

---

### Post by ryu kun on 2010-09-18
I also have tried anything in the first post but none of them did work for me either. 
Removing shutdown button may work but is there really not any other (more "proper") solution for this?

---

### Post by hasi42 on 2010-09-27
> **ryu kun said:**
> I also have tried anything in the first post but none of them did work for me either. 
Removing shutdown button may work but is there really not any other (more "proper") solution for this?

Unfortunately, I haven't found one yet.
I'm also not completely satisfied with my "solution" as the System menu still offers a "Shutdown" entry which appears to be beyond my control. Is there anyone who knows how to get rid of it?

---

### Post by jk-menifee on 2011-02-13
I found this while searching around to solve the same problem:

[https://bugzilla.gnome.org/show_bug.cgi?id=621581](https://bugzilla.gnome.org/show_bug.cgi?id=621581)

Turns out the PostSession script is supposed to run on shutdown or restart as well as logoff, and the outcome of the bug report was a commit to fix the issue. So in a version or two or three we'll all have it working.

John

---

