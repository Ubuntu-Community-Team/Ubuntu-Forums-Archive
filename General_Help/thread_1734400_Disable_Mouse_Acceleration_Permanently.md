---
title: "Disable Mouse Acceleration Permanently"
date: 2011-04-20
forum: General Help
---

### Post by mithril on 2011-04-20
Ok, so this is driving me insane now... :cry:

I use this to set my mouse acceleration off:
```
xinput set-prop 14 273 -1
```It works but... I have to do this after every boot cuz it doesn't save any of my settings.

I tried to edit /etc/init.d/rc.local and /etc/rc.local and I added those scripts there but nothing happened after reboot. Also, everytime I reboot my mouse changes its ID so it was first 13 then 15, then 14, etc.......

I read ArchLinux guide on how to edit xorg.conf but I just can't figure it out. I just started with Linux :S

---

### Post by ChrisWells on 2011-04-20
I also want to know this, I have x set m 0 0 on my startup list but don't know if it's correct.

If you google ubuntu mouse acceleration disable, there is a site that tells you to change something in the mouse device list, I haven't tried it though- [http://www.linuxlog.org/?p=107](http://www.linuxlog.org/?p=107)

---

### Post by tredegar on 2011-04-20
> I tried to edit /etc/init.d/rc.local and /etc/rc.local and I added those scripts there but nothing happened
It won't, because your command needs to be run as the user yourself, once X is running, and those scripts are run as root, without X

What you need to do is put your command in a file called **nomouseacc**
Make it look line this```
#!/bin/bash
#wait for the desktop to settle
sleep 5
# turn off mouse acceleration
xinput set-prop 14 273 -1
```
Make the file executable with **chmod +x nomouseacc**
Then add it to System Preferences Startup applications.

It will be run every time you login.

---

### Post by mithril on 2011-04-20
Thanks I got it fixed! =)

First I realized it's possible to refer to a device as 'pointer: Device Name' so it doesn't matter if it changes ID. (I also had two devices: a pointer and a keyboard, with the same exact name)

So that's how you create Batch-files for linux! I had tried same thing but without #!/bin/bash and also without chmod +x :D

Thank you both.

---

### Post by Swashy on 2011-05-10
> **tredegar said:**
> It won't, because your command needs to be run as the user yourself, once X is running, and those scripts are run as root, without X

What you need to do is put your command in a file called **nomouseacc**
Make it look line this```
#!/bin/bash
#wait for the desktop to settle
sleep 5
# turn off mouse acceleration
xinput set-prop 14 273 -1
```
Make the file executable with **chmod +x nomouseacc**
Then add it to System Preferences Startup applications.

It will be run every time you login.

How do you make a command file with these instructions?

---

### Post by moki12 on 2011-06-16
hi,

firstly thanks for the info provided here, secondly i have further refined the script ..

i found that even the numerical value for a device driver property can and does change..  BUT they can be reffered to by name

so currently i use the following script:

> #!/bin/bash
#wait for the desktop to settle
sleep 5
# turn off mouse acceleration
xinput set-prop 'Razer DeathAdder' 'Evdev Middle Button Emulation' 0
xinput set-prop 'Razer DeathAdder' 'Device Accel Profile' -1
xinput set-prop 'Razer DeathAdder' 'Device Accel Velocity Scaling' 1

this works regardless of device id changing or property id changing

as for how to create script, thought i guess you know by now, create a new file, insert the above script, save it, allow it to be executed as a program, chmod in terminal or right click>properties on it, then add it to list of start-up programs.

---

### Post by moki12 on 2011-06-29
oh yeah, sorry, this really should be mentioned for completion:

use
xinput -h
in terminal for a list of xinput commands

we want:
xinput list 
which will display input devices with their device ID in brackets

and then
xinput list-props #
where # is the device name or device ID. this lists configurable device settings and their numerical ID in (brackets)  

then use: 
xinput set-prop deviceID settingID value
replacing deviceID and settingID with their corresponding numerical values, and value with the new value you wish to set for the variable. (ie. -1 for AccelProfile)

you can then test this has worked by repeating:
xinput list-props deviceID

when you add it to the script, refine it to refer to your device by name and the setting by name so when their values change your script still works (replace numerical value with precise device/setting name, as displayed using xinput list and xinput list-props)

check in terminal whether you can apply the desired change using 
xinput set-prop 'device NAME' 'setting NAME' value

then when it works, create a script out of it as shown in this thread

---

### Post by canakas on 2011-10-22
Thanks for the help everyone!

I had to modify the script slightly to do what I wanted which was to slow down the mouse permanently (not sure I disabled all acceleration).

In addition to the fact that both device IDs and property IDs change, since I have a Logitech M505 which uses their new unified receiver, the pointer entry and the keyboard entry will share the same name in xinput --list.

This is solved by stating the device name with a prefix, as in pointer:devicename or keyboard:devicename


```
#!/bin/bash
#wait for the desktop to settle
sleep 5
# adjust mouse acceleration
xinput set-prop 'pointer:Logitech USB Receiver' 'Device Accel Constant Deceleration' 2.5
xinput set-prop 'pointer:Logitech USB Receiver' 'Device Accel Adaptive Deceleration' 15
xinput set-prop 'pointer:Logitech USB Receiver' 'Device Accel Velocity Scaling' 9

```

EDIT: Well the effect vanishes upon suspend/sleep -> wake - the script should probably go somewhere else than startup scripts...

---

