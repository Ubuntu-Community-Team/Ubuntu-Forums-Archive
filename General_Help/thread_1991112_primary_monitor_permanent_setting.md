---
title: "primary monitor permanent setting"
date: 2012-05-30
forum: General Help
---

### Post by then_dude on 2012-05-30
hello everybody,  i got a dual screen, and i can read everywhere on the internet that it takes   xrandr --output HDMI1 --primary  to make my hdmi1 the primary screen. I type this every time i start Ubuntu. but nowhere i can find anything on an option to make this permanent;   can anybody help me?   thanks

---

### Post by marrok1 on 2012-05-30
you could always write a shell script that does it for you and set it to run on startup

---

### Post by then_dude on 2012-05-30
thanks

i thought so, 

i'm not good at this, so a few more questions

the shell script, should it be run as

 
[LIST=1]
[*]The [upstart]("http://upstart.ubuntu.com/") system will execute all scripts form which it finds a configuration in directory /etc/init.   These scripts will run during system startup (or in response to  certain events, e.g., a shutdown request) and so are the place to run  commands that do not interact with the user; all servers are started  using this mechanism.  You can find a readable introduction to at: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html) the man pages man 5 init and man 8 init give you the full details.
[*]A shell script named .gnomerc in your home directory  is automatically sourced each time you log in to a GNOME session.  You  can put arbitrary commands in there; environment variables that you set  in this script will be seen by any program that you run in your session.   Note that the session does not start until the .gnomerc script is finished; therefore, if you want to autostart some long-running program, you need to append & to the program invocation, in order to detach it from the running shell.
[*]The menu option *System -> Preferences -> Startup Applications*  allows you to define what applications should be started when your  graphical session starts (Ubuntu predefines quite some), and add or  remove them to your taste.  This has almost the same purpose and scope  of the .gnomerc script, except you don't need to know sh syntax (but neither can you use any sh programming construct).
[/LIST]

i guess the best way to run it is as  a startup application ? 

thanks

---

