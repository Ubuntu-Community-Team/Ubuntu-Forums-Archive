---
title: "How to export per-user process variables?"
date: 2010-03-15
forum: General Help
---

### Post by amn108 on 2010-03-15
Hi all.

I can't seem to find how to export a variable to all processes I run under my user? I have an application that needs this variable, and currently I have to manually export this variable (typing "export VAR=... in terminal) every time before I run the application.

Which profile file I have to put the export expression into? I want all processes to inherit this variable, not just the shell/terminal. I.e. a true environment variable...

---

### Post by gmargo on 2010-03-15
From the bash man page:
> 
       When bash is invoked as an interactive login shell ... it first reads and executes commands from the file /etc/profile, if that file exists.  After reading that file, it looks for ~/.bash_profile,  ~/.bash_login,  and  ~/.profile,  in  that  order, and reads and executes commands from the first one that exists and is readable.
Typically, your ~/.profile invokes ~/.bashrc.  The ~/.bashrc is the best place to put your environment variables.  Log out then in and all processes will now have those variables.

---

### Post by amn108 on 2010-03-15
Ok, I will try that (I think I even did?!).

However, wouldn't variables setup through ~/.bashrc only be available to processes actually started by bash? What about processes started by GNOME directly or even 'init'?

---

### Post by gmargo on 2010-03-15
> **amn108 said:**
> Ok, I will try that (I think I even did?!).

However, wouldn't variables setup through ~/.bashrc only be available to processes actually started by bash? What about processes started by GNOME directly or even 'init'?
Your GNOME session gets started by bash. (More specifically, by a "login shell" - which is bash unless you've set it to something else.)

Update: now I'm not so sure I'm right.  I'm trying to test this but having a hard time coming up with a way to view the system's environment without invoking another shell.

---

### Post by gmargo on 2010-03-15
Ok, I think I've got this figured out.  I was wrong about the $HOME/.bashrc; it does not get invoked by the shell that starts gnome-session.  However, $HOME/.profile does (not sure why it doesn't call $HOME/.bashrc though), so environment variables placed in $HOME/.profile will be inherited by gnome-session.  Another way is to add a script to /etc/profile.d/ - environment variables exported by scripts in that directory will be inherited by gnome-session as well.

So go ahead and add your special environment variables to $HOME/.profile (or /etc/profile.d/ if you want to set it for all users.)

For future reference, the environment of any process can be inspected from a special file in the /proc file system: /proc/_processid_/environ.  The strings in that "file" are null terminated so to view it use tr to translate.  For instance, for the gnome-session process, use ps to find the process id:
```

$ ps -efw | grep gnome-session
gmargo    1617  1572  0 12:35 ?        00:00:00 gnome-session
[other stuff snipped]

tr '\0' '\n' < /proc/1617/environ | sort > /tmp/env.gnome-session.txt

```

---

### Post by amn108 on 2010-03-16
I have just exported the variable from ~/.bashrc which made it appear in GNOME terminal, for instance.

However, I have this application - SciTE - which has its own terminal, and it is not there :-(

I will try .profile now, but I doubt that will do it, as I think I have tried it before.

I have tried to trace the origins of the "scite" process, and through System Monitor in Ubuntu, it shows it right at the root of the process tree, NOT under gnome-session process, which to me suggests it is not started by gnome-session, which is very weird indeed. I start the application by hitting Alt+F2 ("Run Application") and typing "scite".

---

### Post by gmargo on 2010-03-16
> **amn108 said:**
> I have just exported the variable from ~/.bashrc which made it appear in GNOME terminal, for instance.

However, I have this application - SciTE - which has its own terminal, and it is not there :-(

I will try .profile now, but I doubt that will do it, as I think I have tried it before.

I have tried to trace the origins of the "scite" process, and through System Monitor in Ubuntu, it shows it right at the root of the process tree, NOT under gnome-session process, which to me suggests it is not started by gnome-session, which is very weird indeed. I start the application by hitting Alt+F2 ("Run Application") and typing "scite".

Anything started by the Gnome run-application will be originally parented by gnome-session (or a decendent).  But a process can always detach from its parent and become owned by init (aka the root of the process tree.)

Try the $HOME/.profile change (be sure to export) and use the method outlined above to see SciTE's environment.

---

### Post by amn108 on 2010-03-16
Exporting through ~/.profile works fine ;-)

---

