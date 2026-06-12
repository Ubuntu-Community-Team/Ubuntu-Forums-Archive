---
title: "Can't seem to suspend to RAM"
date: 2006-03-17
forum: General Help
---

### Post by matts0344 on 2006-03-17
I installed the GNOME power management utility as suggested when I searched for this problem. I checked it to suspend when I press the power button. 

When I press the power button it goes to a black screen with white writing that says:

[name of my computer] login: 

Then it just sits there for about 10 seconds and powers off.

I really like suspend to RAM because I don't want to leave my computer running all the time but its great to be able to 'boot' in about 5 seconds. 

By the way Windows XP has no problem suspending so I don't think its a hardware problem. Any suggestions? Has anyone got suspend to work in Breezy on a desktop?

Thanks for any help you guys you give. This forum rules and so does Ubuntu!

---

### Post by matts0344 on 2006-03-17
OK, update, I did what it says on this page:[https://wiki.ubuntu.com/SuspendHowto]("https://wiki.ubuntu.com/SuspendHowto")

Now, when I go to logout it has the option to suspend the computer. When I select it the computer fades out and appears to go into standby, however, when I press the power button to resume all I get is flashing white with vertical lines on the screen.

---

### Post by matts0344 on 2006-03-18
Anybody have any idea on how to suspend to RAM with the fglrx drivers?

I neeeed suspend to RAM :cry: 

All I get is flashing white lines when I resume. Tried turning ACPI=off and APM=on in the GRUB config as suggested in other threads but it doesn't do anything.

Any other suggestions.

I'm using an ATI Radeon 9600 with the newest fglrx drivers ( 8.23 I believe) in Breezy.

---

### Post by rfruth on 2006-03-18
I to struggled with suspend to RAM on my mini tower, finally got it working, had to edit my acpi-support file as described here [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Suspend_to_memory]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Suspend_to_memory")

---

### Post by magisterludi on 2006-03-18
To wake the fglrx driver its state needs to be written on the
harddisk when initiating suspend and then when resuming
fetched back

comment in this in your /etc/acpi/prepare.sh (if it isn't already)
```

if [ x$SAVE_VBE_STATE = "xtrue" ]; then
  VBESTATE=`tempfile`
  vbetool vbestate save >$VBESTATE;
fi

```

and set SAVE_VBE_STATE in your /etc/defaults/acpi-support on true:
```

SAVE_VBE_STATE=true

```

be sure you have vbetool installed

---

### Post by matts0344 on 2006-03-18
How do I tell if vbetool is installed?

---

### Post by magisterludi on 2006-03-18
open an terminal and type "vbetool"
or do "apt-get install vbetool" or install it via
synaptic

---

### Post by matts0344 on 2006-03-18
Well, that didn't change anything, I still get those flashing white lines when I resume from standby. I checked and I do have vbetools installed. Any other ideas?

---

### Post by magisterludi on 2006-03-19
may be this is commented out in your /etc/acpi/resume.sh:
```

if [ x$SAVE_VBE_STATE = xtrue ]; then
  vbetool vbestate restore <$VBESTATE
fi

```

If not check the changes above again.

Btw. the lines will always be there if you resume
but then when properly configured disapear.

You may try to activate this in you /etc/defaults/acpi-support:
```

DOUBLE_CONSOLE_SWITCH=true

```

---

### Post by matts0344 on 2006-03-19
Well ok, now it does return from suspend after the white lines (about 15-20 seconds after). I was hoping it would return instantly like XP but I'll settle for those over booting. BUT now there is another problem, when returning from standby the system in unbareably slow (very high CPU usage), like you can hardly do anything, the system takes about 5 minutes to restart. 

Why would this be happening? Maybe this issue will be fixed in Dapper?

---

### Post by magisterludi on 2006-03-20
I have this behaviour sometimes, too. I haven't tried to figure it out yet.
Maybe it is because of gnome. The update-notifier gives some trouble
sometimes.
If you don't want to make a hard reset press ALT+PRINT+S then wait
a second and then press ALT+PRINT+B which will trigger the SysRQ
and sync your hard disk before it  reboots.

---

