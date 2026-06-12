---
title: "Ubuntu - Terminal is running after restart but is 'hidden'"
date: 2011-11-08
forum: General Help
---

### Post by matan7779 on 2011-11-08
I place this script in rc2 directory:

#!/bin/sh -e
echo 123>>/home/qa/1.txt
gnome-terminal -e /home/[user]/Desktop/Tester.pl


If I run it manually it works great (a new terminal is opened and running the script and terminal stays open).

When I perform Restart (power reset), file "1.txt" is created successfully but the terminal is not "stays open" and I do not see it.....

What shell I do to run a Perl script on terminal and it will stay open after restart?!

After 2 days I am realy desperate :(
Thanks a lot.

Can you advice?

Thanks a lot…
Matan

---

### Post by btindie on 2011-11-08
You **don't** place normal shell scripts in the /etc/rc2.d directory, they are sym links to Sys-V init scripts which are located in /etc/init.d.

If you want a GUI application to run on startup then run *gnome-session-properties* and add it to that.

Normal non-GUI applications can be added to /etc/rc.local

---

### Post by matan7779 on 2011-11-08
Actually i place it also in the init.d ald also in the rc2.d but it runs also it the file in init.d is not exists.

BUT, I did not realy understand the GUI you talk about.
After PC restart, the script run, the File 1 is created but the Terminal is not seen.

So can you explain again (sorry I am new in using Linux machines..) what shell I do so the script Tester.pl will run the the terminal will be open?


Thanks a lot
Matan

---

### Post by mcduck on 2011-11-08
You can't start a graphical application from init scripts, as there is no graphical environment running at that point. The terminal will not be able to open, instead it just creates an error message about display not being available.

If you want a graphical application to start automatically, you'll need to do that using some of the startup scripts in your home directory. For example ~/.profile is executed when you log in, so adding your script there should work.

---

### Post by matan7779 on 2011-11-08
Sorry,
I still dont get you when you say "graphical application".
I am not running any graphical app.
I only run gnome terminal.
Now, If you means that the gnome terminal is the GUI and I need to wait untill OS/PC is up, can I make any kind of delay so the system  will be up and only then it will run the GUI/terminal?

Thanks, thanks, thanks,
:)
Matan

---

### Post by btindie on 2011-11-08
Gnome is the GUI and gnome-terminal runs from within it, it's a graphical application.

You need to use *gnome-session-properties* to add programs to be ran when you login.

So when the desktop is up and running open a gnome terminal and type *gnome-session-properties*. That will present you with a box that allows you to specify additional programs to be run.

---

### Post by mcduck on 2011-11-08
> **matan7779 said:**
> Sorry,
I still dont get you when you say "graphical application".
I am not running any graphical app.
I only run gnome terminal.
Now, If you means that the gnome terminal is the GUI and I need to wait untill OS/PC is up, can I make any kind of delay so the system  will be up and only then it will run the GUI/terminal?

Thanks, thanks, thanks,
:)
Matan
Gnome-terminal *is* a graphical application, the commands and programs you run *inside* the terminal are command-line applications. They have no windows or other graphics, only text. Gnome-terminal of course has a pretty window, graphical settings dialog where you can click around with a mouse, scrollbars etc, all those are graphical stuff.

Anyway, it is possible to add a delay to your command (just use the sleep command for that), but you'll also need to specify a display where the gnome-terminal window should open (as you are launching it from outside of any graphical environment). And in th end the terminal would end opening running as the rot user, as that's the suer account that executes the commands from init scripts.

It really would be much simpler, and cleaner, to just add your script command into ~/.profile instead. That way you don't need to estimate the correct delay, mess with permissions, or handle exporting the display variable to tell where the gnome-terminal window should open.

---

