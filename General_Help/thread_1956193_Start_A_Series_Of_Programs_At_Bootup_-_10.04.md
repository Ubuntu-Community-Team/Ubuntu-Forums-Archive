---
title: "Start A Series Of Programs At Bootup - 10.04"
date: 2012-04-10
forum: General Help
---

### Post by Spaceman Spiff on 2012-04-10
Hello all,


  I am interested in starting a series of programs the moment Ubuntu finishes booting up.  Below I display what I think is the proper procedure, but differing procedures would be greatly appreciated!

Currently:
[LIST=1]
[*] Boot up ubuntu, and do not startx. (Achieved this with grub property)
[*] Automatically login (Using [[COLOR="Blue"]this[/COLOR]]("http://tombuntu.com/index.php/2010/01/01/enable-automatic-login-in-ubuntu-9-10-server/") procedure)
[*] Start screen -S "Name"  (Still haven't done this)
[*] Start my programs once screen runs (Still need to do this)
[*] If program crashes start it again (Still need to do this)
[/LIST]

Any advice/links would be greatly appreciated!  I am googling as we speak, but I'm unsure of what I'm looking for.

Constantin

---

### Post by 1clue on 2012-04-10
What sort of programs are you trying to run?

If you're talking about LibreOffice and Evolution then it's one thing, but if you're talking about services then it's another.

I'm not sure what Unity uses, but a traditional window manager uses .xsession in your home directory to do anything a user wants when they log in.

I strongly recommend that you not automatically log in, but it's a free world so you can throw your security out the door if you choose to.

If you're talking about a service, then there are two common approaches, depending on how you want it to behave:
[LIST=1]
[*]make an init script for it in /etc/init.d
[*]put it directly in /etc/inittab
[/LIST]

I strongly recommend a backup before you start messing with /etc/inittab.

---

### Post by papibe on 2012-04-10
Hi Spaceman Spiff.

You can use the '@reboot' tag in crontab, and set a crontab that looks something like this:
```
# m h  dom mon dow   command
@reboot   screen -dmS  MyScreenName  /path/to/myscript.sh
```
If running something like this is your main priority, you don't really need the automatic login part.

I hope that points you in the right direction. Tell us how it goes.
Regards.

---

### Post by Spaceman Spiff on 2012-04-10
Hi 1clue, I appreciate your response.

There is no need for security, this is not a typical house hold application.  This is an onboard system that needs to boot up and start working immediately.

There is no .xsession, I have prevented x from starting ... I hope (or am I mistaken?)

I will take a look into init.d, I appreciate the advice.  Perhaps I need to look into bash scripting as well?

---

### Post by Spaceman Spiff on 2012-04-10
Hey papibe, this is great! I figured I would need to use cron.

An important thing to note though, I was hoping to seperate the screen -S and my other calls.  My other calls would look like:

[LIST=1]
[*] gpsd /dev/ttyS0   (This is a daemon and immediately begins in the background)
[*] bin/MyScript1 &    (This needs to start, and be run in the background)
[*] bin/MyScript2      (This stays in the fg, displaying status messages)
[*] if MyScript2 crashes, stop MyScrip1, go to (2)
[/LIST]

Also, what do you mean by if this is my priority?  What would my other option be?  Starting the screen in the crontab?

---

### Post by papibe on 2012-04-10
If I understand correctly, you could call a script on crontab:
```
# m h  dom mon dow   command
@reboot  /path/to/script.sh
```
And script.sh would be:
```
#!/bin/bash

# This is a daemon and immediately begins in the background
/full/path/to/gpsd /dev/ttyS0

# This needs to start, and be run in the background
/full/path/to/bin/MyScript1 & 

# This stays in the fg, displaying status 
/full/path/to/bin/MyScript2

# other stuff
screen -dmS  MyScreenName  /path/to/other_script.sh
```
Something like that?
Regards.

---

### Post by Spaceman Spiff on 2012-04-10
Hey papibe,

I've been playing around with crontab after you made your suggestion.

I think my current method is:
```

@reboot screen -d -m -S "MyServer" /bin/bash

```

Is this okay?  I had to /bin/bash because I would reattach to my session and no shell preferences would be set.

On that screen, it logs into bash, so I'm assuming my .bashrc will be called.  I will execute from there.

Papibe does your approach run my .bashrc?  I have some shell variables I need to set.

Thank you so much for the help.

Constantin

---

### Post by 1clue on 2012-04-10
I'm a bit confused.

In some ways you seem to want an embedded processor application, in some ways a server for a normal installation, and in some ways you seem to want to interact with a user.

Inittab is essentially the heart of the Linux system.  What SS is posting describes this aspect of it perfectly, it enables you to have a process that will be rapidly restarted if it fails or quits for any reason.  This would be good for some sort of embedded controller.  The disadvantage of that is that your process needs to work perfectly and the starter script needs to return almost immediately or it raises problems with the rest of the system.

A "normal" service would be started through /etc/init.d, and be startable and stoppable at boot or at any other time.  The lion's share of Linux services work this way.

I would say that if you intend to develop something like this then you should bone up on bash or whatever other scripting language you might need.

---

### Post by Spaceman Spiff on 2012-04-11
I have achieved my goal using a bash script and rc.local

```

su - constantin -c "screen -d -m -S MyServer /home/constantin/Applications/MyServerStartup.sh"

```

Crontab was giving me strange errors and situation, and worked intermittantly.

The weird thing was I had to set up my paths in the script, I couldn't get it to load my regular paths.  Also, I cannot ctrl-z from the script and enter a shell inside the screen window.

Constantin

---

### Post by 1clue on 2012-04-13
Services do not load your normal user environment.  That goes for inittab, /etc/init.d scripts and crontab scripts.  That's by design.

Also, running an interactive app directly by any of these approaches is sketchy at best.  Interactive apps controlled by inittab (xdm and equivalents are the only ones I can think of) are designed specifically for that.

---

