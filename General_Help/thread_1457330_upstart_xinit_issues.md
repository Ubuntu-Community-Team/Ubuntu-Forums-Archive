---
title: "upstart xinit issues"
date: 2010-04-18
forum: General Help
---

### Post by forshee on 2010-04-18
I'm pretty new to Linux so hopefully this is an easy fix. I'm having a lot of problems with a rather simple upstart script. The code is as follows.[INDENT]start on runlevel [2]
[/INDENT][INDENT]stop on runlevel [0316]
[/INDENT][INDENT]exec xinit *my_client *
[/INDENT]The script runs (I also have it touch a file to confirm this) but my program wont start. The same code works from the command prompt so the program is working. The ethernet has to be up and some other minor scripting in interfaces has to be run before the program starts or it will crash. I think this is what is happening.
What can I use for my start on events? I'd prefer it to run after login ( I am using an auto login script so things might be a bit odd there). And I'm trying to do this without the gdm or a window manager as its a pseudo embedded project and we don't have a lot of space or power to work with.

---

### Post by klemes on 2010-04-18
Where did you placed this script and how did you name it?I would place it in /etc/rcS.d and name it with something looking like S(xx+1)my_startup_script.sh (without the brackets)where xx the number the networking start script in the same directory uses in it's name

ie my /etc/rcS.d has a file named S40networking.Then I would name my script S41my_script.sh and place it in the same directory.
Also do not forget to make it executable by giving:sudo chmod + x S41my_script.sh.

---

### Post by forshee on 2010-04-18
The script is /etc/init/pce.conf which from what I've read is the place to put all the new upstart scripts.  It looks like your talking about the rc scripts right? I was under the impression that those were being phased out and replaced with upstart. The chmod and ownership are all set the same as everything else in the folder so I don't think that is it.

---

### Post by klemes on 2010-04-18
You must be right but I can not verify this as I am writing this from an old system running Ubuntu 7.10.Sorry for the inconvenience.
Maybe if you were willing to downgrade a little I could help you:lolflag:
or maybe wait till I am back to my main system running 10.04 and figure out how the new init scripts work :guitar:.:P
But seriously now sorry mate can't help you for the time being as much as I would like to be able to!!!

---

### Post by forshee on 2010-04-18
Ok I'm looking at this again and I think this is a problem with xinit and not upstart. So I think I'll try another post more accurately describing the problem.

---

