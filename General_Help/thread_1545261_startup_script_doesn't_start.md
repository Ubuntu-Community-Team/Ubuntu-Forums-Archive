---
title: "startup script doesn't start"
date: 2010-08-03
forum: General Help
---

### Post by montini on 2010-08-03
Please help me find where's the problem: I followed the instructions on this link:

[http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html]("http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html")

and at the end it says I should put it into "Startup applications" - and I did that, but after I do logout/login, the script doesn't work. It starts to work only if I start it from terminal. What's wrong?

---

### Post by TeoBigusGeekus on 2010-08-03
How exactly did you put it on startup apps? What did you give for command?

---

### Post by Smart Viking on 2010-08-03
try to put this on top of the script:

```
sleep 10
```Which will make the commands execute 10 seconds later, and i think will improve the chances of that it will work. :)

EDIT: And when you put it on startup applications, the command it launch it is it's full path, so if it was located in your Documents directory and was called "file.sh", this would be the command to launch it(no "." in the front):

```
/home/username/Documents/file.sh
```

---

### Post by montini on 2010-08-03
does it have to be "*.sh"? because my running command IS the full path, it's just that the name is only "2fsrl", not "2fsrl.sh"

---

### Post by Smart Viking on 2010-08-03
> **montini said:**
> does it have to be "*.sh"? because my running command IS the full path, it's just that the name is only "2fsrl", not "2fsrl.sh"

no i do not think it have to be a .sh, you could always try but i doubt that will give a different effect, but i always name scripts as .sh files since well thats the proper way, and nautilus will understand that it's a script too and give it a different icon. :)

---

### Post by JohnnyC35 on 2010-08-03
make sure to mark the file as executable as well

---

### Post by kerry_s on 2010-08-03
you should put "#!/bin/bash" at the top.

example:

```
#!/bin/bash
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
```

---

### Post by montini on 2010-08-04
I've put "#!/bin/bash" (it was "#!/bin/sh" before) and the line "sleep 10" afterwards.

I can't explain it - when I do restart, I get never it to work - I must start it manualy - OR, I can do logout/login - and then it works :///

Is there another way to get synaptic touchpad to work with multitouch (two finger) scrolling? I imagine there has to be a way to put those parameters, mentioned in the script, into some original configuration - because "synclient" is just the tool to change them "on the fly"?

---

### Post by kerry_s on 2010-08-04
try putting each command as a start up, which is how i did it when i disabled tap.

click add:
synclient VertTwoFingerScroll=1

click add:
synclient HorizTwoFingerScroll=1

etc...

---

### Post by montini on 2010-08-04
yeah, but that would be the lamest way to do it :) sorry, no offence - it just has to be another "smart" way...

> **kerry_s said:**
> try putting each command as a start up, which is how i did it when i disabled tap.

click add:
synclient VertTwoFingerScroll=1

click add:
synclient HorizTwoFingerScroll=1

etc...

---

### Post by kerry_s on 2010-08-04
> **montini said:**
> yeah, but that would be the lamest way to do it :) sorry, no offence - it just has to be another "smart" way...

try starting over.

first put it in path:
gksudo gedit /usr/local/bin/2fsrl

put:
#!/bin/bash
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48

make it executable:
sudo chmod +x /usr/local/bin/2fsrl

now add it to your startup applications:
name: touchpad script
command: 2fsrl

---

### Post by montini on 2010-08-04
I think it would be more appropriate to try this:

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html]("http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html")

but it is not possible as it seems Ubuntu Netbook Edition (10.04) doesn't contain folder "/etc/hal"

and if I try to use these suggestions:

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html?showComment=1238555940000#c5278758273100263480]("http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html?showComment=1238555940000#c5278758273100263480")

I can't - because there is no "/etc/X11/xorg.conf" in the UNE ://
If I try to create the file from "xorg.conf.failsafe" adding the suggested lines - those I put like these:

```
Section "InputDevice"
  Option "HorizEdgeScroll" "0"
  Option "VertEdgeScroll" "0"

  Option "SHMConfig" "on"
  Option "VertTwoFingerScroll" "1"
  Option "HorizTwoFingerScroll" "1"
  Option "TapButton2" "3"
EndSection
```

after I kill X (Ctrl-Alt-SysRq-K), ubuntu tells it would load low graphics mode - as some settings in the config are not correct - I assume it's my added Section "InputDevice", as there were no such section in the "xorg.conf.failsafe".

Any thoughts?

---

### Post by kerry_s on 2010-08-04
well hal is on its way out, replaced by dbus.

xorg always been touchy, just been getting worse.

the simple thing is to add the commands 1 by 1 to startup, but you consider that lame. your next best option is to get the script to work, but for some reason it won't. the most common mistake with scripts is typo's & space where there shouldn't be, so check & double check.

your next step would be to install a gui to do it for you, i think the most common 1 is "gpointing-device-settings".

---

### Post by montini on 2010-08-04
an update: now I really suspect it has something to do with maybe default keyring or smth. Explaining:

The script actually works when I do logout/login sequence. But it doesn't work when I restart my netbook - and the difference is - I made my login to be "login automatically" - as I don't want to enter the password everytime. Does this give any new thoughts? (oh, and the script is in the /home/montini/ folder)

By the way, kerry_s - I tried to enter every line separately to my "Startup Apps" - this doesn't make any change - it works when I do logout/login, but not when I restart. The "pointing-device-settings" doesn't work - I mean when I mark the checkboxes which are meant to enable two finger scrolling, it doesn't help.

---

### Post by Smart Viking on 2010-08-04
> **montini said:**
> 
The script actually works when I do logout/login sequence. But it doesn't work when I restart my netbook - and the difference is - I made my login to be "login automatically" - as I don't want to enter the password everytime.

Yeah, it is possible that that is causing it, change that setting and see if it works after that. :)

---

### Post by samnardoni on 2010-12-01
I had the same problem as you.

Solution: put it in your .bash_profile in your home directory.

Here's my ~/.bash_profile
```
#!/bin/sh
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=10
synclient EmulateTwoFingerMinZ=48

```

---

