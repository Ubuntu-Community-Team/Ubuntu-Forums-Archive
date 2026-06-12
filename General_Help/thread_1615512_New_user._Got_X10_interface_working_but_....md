---
title: "New user. Got X10 interface working but ..."
date: 2010-11-07
forum: General Help
---

### Post by specter333 on 2010-11-07
Hello.  I'm new to Ubuntu and am in the process of learning and making sure it's going to work for my purposes.  There are some windows apps that I use extensively on a daily basis and I can't seem to find Linux replacements for all of them, but I'm still working on it.

I'm using Ubuntu 10.10 freshly installed.

Here are the apps I'm trying to get working/replaced. 

EventGhost automation tool - Works under wine but doesn't see IR receiver or Gyration Air mouse.

AutoHotKey - Found cross platform replacement IronAHK, Seems to work.

X10 home automation - works but not well.

I'm currently concentrating on X10.  I have the CM15a transceiver working by following the instructions here...
```
http://somethinginteractive.com/blog/2009/05/06/guide-x10-cm15a-ubuntu/
```

I can control my X10 modules with launchers, terminal profile, Autohotkey scripts and EventGhost but it ask for my sudo password which is really annoying when I'm only turning on a light.  The command from the install guide is..
```
sudo ./cm15ademo m1 on
``` This command turns my living room lights on.

My noob question is, Is there a way to use this command without using the sudo prefix?  Or is there a way to include the sudo password in the command?

The other part of this which I haven't researched yet is not having the terminal window open when it runs, such as using the /hide in windows command line.  I'm going to start looking for that while I wait for replies to this post.

Thank you for any help you can give me.

---

### Post by Kr0nZ on 2010-11-07
you need to edit your sudoers file and add a line like
```
username    ALL = NOPASSWD: /cm15ademo
```
replace username with your own user name
edit the sudoers file with sudo visudo

[http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/](http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/)
[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

---

### Post by specter333 on 2010-11-07
> **Kr0nZ said:**
> you need to edit your sudoers file and add a line like
```
username    ALL = NOPASSWD: /cm15ademo
```
replace username with your own user name
edit the sudoers file with sudo visudo


Thank you for the info.  I've been working on this for several hours and still can't get it to work.  I did however get a long lesson in restoring your sudoers file when you screw it up.  Very educational.

So, what I have is... I have a couple of terminal profiles ran from launchers and other.  The code to start the terminal window from the launchers is...
```
gnome-terminal --window-with-profile=x10m1on
```

The code from the terminal profile to control the modules is...
```
sudo ./cm15ademo m1 on
```

I can do away with the sudo password altogether but that's not what I want to do.  I haven't been able to do it on a specific command as you suggested.  I believe that I must not be getting the name or the path of the app that sudo sees opening correct, therefore still asking me for a password.  

Any ideas?

I also still have not figured out how to hide the terminal windows when they run.  Help with that would be appreciated too.

Thanks

---

### Post by efflandt on 2010-11-07
For sudoers, if you want to experiment, add a file to /etc/sudoers.d/ (see README there) instead of modifying (and possibly breaking) /etc/sudoers.  You likely need to include the /full_path_to/cm15ademo (not using shortcuts like ~).

Note that if you add a **bin** directory to your home directory (mkdir ~/bin), that bin will be in your path the next time you login.  So you would no longer need to use a path to run cm15ademo or other scripts or programs you put there.  However, you would need a full path for sudoers or to run it from cron.

I have not figured out how to properly format a line in a launcher to redirect stdout and/or stderr, but you could easily have one script handle multiple launchers.  Example assuming you put cm15ademo and this script in your ~/bin or elsewhere in your PATH:

```
#!/bin/sh
date=`date`  #note these are backticks, not single quotes
echo "$date dev: $1 $2" >> ~/test.log 2>&1
cm15ademo $1 $2 >> ~/test.log 2>&1
```That redirects stdout and stderr to a log file so you can tell if it is working.  If the cm15ademo line fails there would be an additional line in the log file after the echo line.

Then you could create a launcher for each thing you want to do with each device using Application instead of Terminal (no terminal needed) running the script like:

```
scriptname m1 on
```sample log (because I do not have cm15ademo):

```
Sun Nov  7 13:11:44 CST 2010 dev: m1 off
/home/efflandt/bin/test2.sh: 4: cm15ademo: not found
Sun Nov  7 13:12:02 CST 2010 dev: m1 on
/home/efflandt/bin/test2.sh: 4: cm15ademo: not found
```Or if you want a script that would not log anything:

```
#!/bin/sh
cm15ademo $1 $2 > /dev/null 2>&1
```

---

### Post by specter333 on 2010-11-07
Thanks for the reply, I'm going to start working on this now and see what I can figure out.  Couple of questions just to make sure I'm understanding you correctly.

> **efflandt said:**
> For sudoers, if you want to experiment, add a file to /etc/sudoers.d/ (see README there) instead of modifying (and possibly breaking) /etc/sudoers.
So I should put a file here and do the modifications on it instead of on /etc/sudoers?  Does it matter what the name of the file is?

Although it was good experience learning how to fix a sudoers file it would be nice to have a backup.  By the way, as I said earlier I'm just trying to learn and this is a fresh install, nothing important on this computer.  So if I screw it up badly enough reformatting and starting again is still an option.

Also, to restore my sudoers file I used the code from [HTML]https://help.ubuntu.com/community/Sudoers[/HTML] which is Ubuntu 8.04.  Is that code the same or close enough to what came with 10.10?


> Note that if you add a **bin** directory to your home directory (mkdir ~/bin), that bin will be in your path the next time you login.  So you would no longer need to use a path 
I've been putting all my apps and launchers in my home directory, the guide for cd15ademo did this so I followed it's example.  Should they go to the /bin instead?

Thanks again for your help.  I'll likely be up all night again trying to learn this stuff but I've learned a lot already.

---

### Post by specter333 on 2010-11-08
Ok, I see what your trying to say and I like the direction it's going.  If I can make it work it would be muuuucccchh simpler to use than a new terminal profile for every little thing I want to do.  But so far I can't make it work.

Here is the log output.
```
Mon Nov  8 00:31:49 CST 2010 dev: m1 on
libusb couldn't open USB device /dev/bus/usb/007/002: Permission denied.
libusb requires write access to USB device nodes.
11/08 00:31:51 X NO Access to CM15A for X10 
Unknown or unavailable command
```

Looking up this libusb thing I see it's a common problem in Ubuntu and, judging by the number of post about it, it's extremely frustrating for Ubuntu users.  USB access such as this must be done through the root, so permissions are still needed.

I see two things to try before giving up on Ubuntu.  1. assigning certain user groups may do the trick, even though it didn't in most post I read. 2. An app called Device::USB which looks like it may allow access to the needed devices.
[HTML]http://search.cpan.org/~gwadej/[/HTML]

Any other ides on this would be appreciated.

---

### Post by specter333 on 2010-11-08
I messed around with user permissions some more and now it's working.  Don't know what I did different though.

Thank you for the help.

---

### Post by sdellutri on 2011-02-03
> **specter333 said:**
> Hello.  I'm new to Ubuntu and am in the process of learning and making sure it's going to work for my purposes.  There are some windows apps that I use extensively on a daily basis and I can't seem to find Linux replacements for all of them, but I'm still working on it.

I'm using Ubuntu 10.10 freshly installed.

Here are the apps I'm trying to get working/replaced. 

EventGhost automation tool - Works under wine but doesn't see IR receiver or Gyration Air mouse.

AutoHotKey - Found cross platform replacement IronAHK, Seems to work.

X10 home automation - works but not well.

I'm currently concentrating on X10.  I have the CM15a transceiver working by following the instructions here...
```
http://somethinginteractive.com/blog/2009/05/06/guide-x10-cm15a-ubuntu/
```

I can control my X10 modules with launchers, terminal profile, Autohotkey scripts and EventGhost but it ask for my sudo password which is really annoying when I'm only turning on a light.  The command from the install guide is..
```
sudo ./cm15ademo m1 on
``` This command turns my living room lights on.

My noob question is, Is there a way to use this command without using the sudo prefix?  Or is there a way to include the sudo password in the command?

The other part of this which I haven't researched yet is not having the terminal window open when it runs, such as using the /hide in windows command line.  I'm going to start looking for that while I wait for replies to this post.

Thank you for any help you can give me.

@specter333 
You indicated you were able to get EventGhost working under Wine.  Can you please advise how you were able to do it?  I would really love to get this working on my system.  I was able to get past the GDI+ Dll for the installation, but now when I try to run it, it just fails and writes the following to the log.txt file.
THANKS IN ADVANCE FOR YOUR HELP!

```

Traceback (most recent call last):
  File "EventGhost.pyw", line 30, in <module>
  File "C:\Program Files\EventGhost\eg\__init__.py", line 114, in <module>
    import Core
  File "C:\Program Files\EventGhost\eg\Core.py", line 277, in <module>
    eg.app = eg.App()
  File "C:\Program Files\EventGhost\eg\__init__.py", line 50, in __getattr__
    mod = __import__("eg.Classes." + name, None, None, [name], 0)
  File "C:\Program Files\EventGhost\eg\Classes\App.py", line 34, in <module>
    ShutdownBlockReasonCreate = _user32.ShutdownBlockReasonCreate
  File "ctypes\__init__.pyc", line 366, in __getattr__
  File "ctypes\__init__.pyc", line 371, in __getitem__
AttributeError: function 'ShutdownBlockReasonCreate' not found

```

---

### Post by stephencoloney on 2012-02-12
> **specter333 said:**
> Hello.  I'm new to Ubuntu and am in the process of learning and making sure it's going to work for my purposes.  There are some windows apps that I use extensively on a daily basis and I can't seem to find Linux replacements for all of them, but I'm still working on it.

I'm using Ubuntu 10.10 freshly installed.

Here are the apps I'm trying to get working/replaced. 

EventGhost automation tool - Works under wine but doesn't see IR receiver or Gyration Air mouse.

AutoHotKey - Found cross platform replacement IronAHK, Seems to work.

X10 home automation - works but not well.

I'm currently concentrating on X10.  I have the CM15a transceiver working by following the instructions here...
```
http://somethinginteractive.com/blog/2009/05/06/guide-x10-cm15a-ubuntu/
```

I can control my X10 modules with launchers, terminal profile, Autohotkey scripts and EventGhost but it ask for my sudo password which is really annoying when I'm only turning on a light.  The command from the install guide is..
```
sudo ./cm15ademo m1 on
``` This command turns my living room lights on.

My noob question is, Is there a way to use this command without using the sudo prefix?  Or is there a way to include the sudo password in the command?

The other part of this which I haven't researched yet is not having the terminal window open when it runs, such as using the /hide in windows command line.  I'm going to start looking for that while I wait for replies to this post.

Thank you for any help you can give me.
Hi there.  I'm a new user based in London and am wondering if you got EventGhost working?
I'm looking for someone to help me develop an EventGhost app that launches a Skype call upon recieving a command from pressing a button on a simple IR remote control.
Can you help with that or know someone who can?
Many thanks,
[email]stephen.coloney@gmail.com[/email]

---

