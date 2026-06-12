---
title: "[Advanced] How would you &quot;trap&quot; GDM shutdown?"
date: 2011-05-28
forum: General Help
---

### Post by Zakhafr on 2011-05-28
Hello everybody, and sorry in advance for the "long" post!

I'll try to describe first what I would like to achieve, then the investigations I made and the solution I came up with.
The goal of the post being to gather some advise, and possibly a better solution that the one imagined.

**_The requirements:_** from time to time, I need to SSH on my mother's PC (68 years old, and she is using GNU/Linux!).
Although she is quite confortable with Ubuntu, my mother is not a computer expert, and she has no clue on how to know whether I have a SSH session or not, so she might shutdown her PC at any moment.
Obviously, if I was doing some backup, cleaning, installations on her PC through SSH, the actions I was doing get killed in the process.
Thus, what I would like is a mechanism to let her know I am working on her PC at that moment, and give her 3 choices:
- Confirm the shutdown (after all, it is HER PC!)
- Cancel the shutdown (and continue with her current session)
- Do nothing, and I'll be warned and shutdown her PC myself (or auto-shutdown when there is no more SSH session)
Note that this sort of feature exists when you have another local session opened on your PC (but not for a SSH session).
When so, if you try to switch off the PC, you would get a dialog box warning you that there is another user with an active session on your PC, and asking you for this user password to confirm the shutdown.

_**Possible cinematic**_
I imagine something as little disruptive as possible on the existing cinematic (I'm speaking of classic Gnome Panel, as my mother runs on Lucid).
-1 ) Click on the "session" applet (the one on top right by default)
-2 ) The menu displays
-3 ) Click on shutdown
-4 ) [TRAP] if there is no SSH session, continue the normal cinematic (step 8 )
-5 ) [TRAP] ... when a SSH session exists, warn the user about that and give choice : Confirm shutdown/Cancel shutdown [do nothing]
-6 ) [TRAP] ... if the user Cancels the shutdown... he/she returns to the active session (as if he/she never choosed Shutdown on the session applet menu)
-7 ) [TRAP] ... else, the user confirmed the shutdown, the normal cinematic resumes (next step)
-8 ) The dialog "Do you confirm shutdown" appears
-9 ) The PC shuts down (if confirmed, eitherwise you return to active session)

The steps marked as [TRAP] are the new steps in the cinematic. The other steps are the existing ones (for default shutdown, when no other user is in local session).

The "TRAP" also adds a feature to autoshutdown when the last active SSH session terminates, as long as the user in session do not hit Confirm/Cancel on the dialog box.



_**Investigations so far**_
I can very easily do the "trap" with a simple bash script.
I have seen a lot of post asking how to run a bash script upon session logout. The problem is neither of the standard possibilities I saw fulfill the requirements, because they occur once the Shutdown is confirmed, and there is no way to cancel it. You could just delay it till the SSH session is over.
The two standard things are:
- The init System V process: add a script in rcX.d
- The GDM PostSession script (located under /etc/gdm/PostSession)

There could also be a possibility: replace the session applet by one of my own with the same icon. The problem is then that I would have to handle all of the 8 options of the menu, and it gets much more complicated because this menu is in fact dynamic (as far as I understood reading pieces of the C code of the applet). Replicating the exact behaviour of the applet to keep the same cinematic could be quite a headache.

Then I noticed that when you hit one of the options "Switch user, Logout, Shutdown, Restart", the systems relys on the small program gtk-logout-helper to do the job. Displaying the help of this program gives a clue on what happens:
```
$ /usr/lib/indicator-session/gtk-logout-helper --help
Usage:
  gtk-logout-helper [OPTION&#8230;]  - logout of the current session

Help Options:
  -h, --help               Show help options
  --help-all               Show all help options
  --help-gtk               Show GTK+ Options

Application Options:
  -l, --logout             Log out of the current session
  -s, --shutdown           Switch off the entire system
  -r, --restart            Restart the system
  --display=DISPLAY        X display to use

```
So it's easy to guess that FastUserSwitch bonobo applet (the one behind the standard session applet) calls this program with the relevant option according to the option clicked on the menu.

Then gtk-logout-helper displays a dialog box with message and icon according to the option it had and does the job.

So I tough: quite easy, let's just rename gtk-logout-helper to gtk-logout-helper-save, put my script in and name it gtk-logout-helper, and it would get launched instead of the usual program and do the trick.

Unfortunately... it does not!
I assume the executable is launched with a call that do not support something else that a REAL executable, such as execcl, execle, execv, and not something like execlp, execvp which would have launched the script.

So I dug deeper to figure out where this exec was, and if it would be possible to patch it to the right flavor of exec (or fork equivalent).
My investigations led me to the conclusion (an expert my be able to confirm wether I'm right or wrong) that the applet does not launch gtk-logout-helper itself, but ask to DBUS to launch it.
... so I stopped there because I wouldn't dare patching DBUS.:p


_**Where are we now**_
so now I'm left to the point where my only (?) option is to write a small C program that would spawn my script. This program would replace the existing gtk-logout-helper, which would be executed in turn if there happens to be no SSH session.



_**And the question is...**_
although writing such a small C program is not that complicated (there might already exist such generic program that would, for example, search for "name_of_myself.sh" in the same directory, and if it exists, bash it!), I was wondering if you experts would have a better idea/solution that would satisfy the requirements.


Many thanks to you all in advance.

---

