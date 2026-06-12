---
title: "Run terminal command at startup"
date: 2010-08-25
forum: General Help
---

### Post by Mugsy323 on 2010-08-25
I know this has been asked a 1000 times, but none of the solutions I've read so far work.

I need to run the following terminal command every time Ubuntu (10.04 64bit) starts:

```
xset m 9 1
```

This boosts mouse speed to maximum. I don't know why, but it is the only thing that works. All built-in mouse settings are at maximum, yet my mouse crawls across the screen when Ubu starts. 

So far, I have tried:

Creating a startup script called "/etc/init.d/autorun.sh" containing
```
/usr/bin/xset m 9 1
```
and when that didn't work...
```
exec /usr/bin/xset m 9 1
```
both with and w/o paths.

I added my script to the list of "Startup Applications".
I tried applying "chmod +x autorun.sh"
I tried putting the command in "etc/init.d/rc.local".
I tried putting the command in "etc/init.d/rcS".

Another tip suggested I use:
```
sudo update-rc.d autorun.sh defaults
```
but that made no difference.

Still, I must run the command by hand every time I run Ubu, and it's getting annoying. Any ideas? Thx.

---

### Post by hakermania on 2010-08-25
1)Create a script which does the command you want to (xset m 9 1) and then try creating a .desktop file in /home/username/.config/autostart that points to this script (Dont forget to make the script executable)

2)If this doesn't work try finding who is responsible for this. Try changing the command xset m 9 1 to something viewable (like echo Hello, I run at startup > /home/$USER/Desktop/StartupFile) and then reboot your PC to see if it worked. If it does so, then the command xset m 9 1 has some problem. Try sleep 10; (sleepo 10 secs) before xset m 9 1 in your script and then reboot again to see if it works..

---

### Post by ajgreeny on 2010-08-25
Without wishing to appear condescending, I presume your script had the proper first line and was made executable?
```
#!/bin/bash
xset m 9 1
```

I don't think there is any point in putting the script in **/etc/init.d** as your xsession has not started at that point so mouse enabling will not have happened at that stage in booting the machine.  It would make more sense to me to add that script to the user Startup Applications list in System->Preferences, as by then the GUI is up and running.

---

### Post by Mugsy323 on 2010-08-25
> **hakermania said:**
> Try sleep 10; (sleepo 10 secs) before xset m 9 1 in your script and then reboot again to see if it works..
Hey, this worked! (the script was already in my autostart folder and did nothing). Not sure why. Big thanks.

---

### Post by WittFan on 2010-09-07
> **Mugsy323 said:**
> Hey, this worked! (the script was already in my autostart folder and did nothing). Not sure why. Big thanks.
Hey Mugsy, I've got the exact same problem. Would you mind posting the contents of your .desktop file and executable script?

---

### Post by Mugsy323 on 2010-09-07
> **WittFan said:**
> Hey Mugsy, I've got the exact same problem. Would you mind posting the contents of your .desktop file and executable script?
First point (and importantly), it's not an "executable" script, just a series of shell (aka "DOS") commands. If you insert "#!/bin/bash" at the top, the rest of the script will be ignored (unless, I believe, you preface each command with "exec"). So if you are using that, don't.

After creating my "script", I went into "System | Preferences | Startup Applications" and "Added" a new entry called "Autorun script", referencing "/etc/init.d/autorun.sh" (my script file), so that Ubu knows to look for it at startup.

Either one alone don't seem to make the script run. You need both.

The "sleep 10" command (wait ten seconds) that "hakermania" told me to use (AFAICT), gives the mouse driver time to load before trying to modify it, so take that into consideration when trying to get your script to work.

Not sure which ".desktop" file you would need that could be of more help. But let me know.

---

### Post by dcstar on 2010-09-08
> **Mugsy323 said:**
> First point (and importantly), it's not an "executable" script, just a series of shell (aka "DOS") commands. **If you insert "#!/bin/bash" at the top, the rest of the script will be ignored** (unless, I believe, you preface each command with "exec"). So if you are using that, don't.
.........

Rubbish, all that top line does is specify the shell environment the script is executed in.

It ensures that the script is run in a known environment rather than whatever may be used depending on the particular setup.

---

### Post by xiboce on 2010-09-08
> **dcstar said:**
> Rubbish, all that top line does is specify the shell environment the script is executed in.


+1

FYI
"#!/bin/bash" is called a "Shebang" line. 
the program loader  takes the presence of the characters "#!" as an indication that the file is a script, and tries to execute that script using the interpreter specified by the rest of the first line in the file aka /bin/bash

---

### Post by Mugsy323 on 2010-09-08
> **dcstar said:**
> Rubbish, all that top line does is specify the shell environment the script is executed in.

It ensures that the script is run in a known environment rather than whatever may be used depending on the particular setup.
Yes, and if you are in the wrong "environment", the commands won't run. Shell commands are not executable programs.

If you are trying to argue my script would run just fine with "#!/bin/bash" at the top, I can assure you it didn't until I removed it.

---

### Post by analoghuman on 2010-09-23
I'm having a similar problem. A shell script set to autolaunch at startup through Startup Applications where xset isn't sticking.

I know it's running since the script also runs a series of xmodmap commands and those changes work fine. It's just that none of the xset settings work. I've tried adding "sleep 10" but it didn't help. The script is attached.

```
#!/bin/sh

xmodmap -e "remove shift = Shift_R"
xmodmap -e "keycode 62 = Up"
xmodmap -e "keycode 114 = Down"
xmodmap -e "keycode 111 = Shift_R"
xmodmap -e "keycode 116 = Right"
xmodmap -e "keycode 105 = Prior"
xmodmap -e "keycode 115 = Next"
xmodmap -e "keycode 112 = Control_R"
xmodmap -e "keycode 117 = End"
xmodmap -e "add shift = Shift_R"
sleep 10
xset r
xset r 62
xset r 105
xset -r 111
#xset r rate 400 40
```

---

### Post by Mugsy323 on 2010-09-24
> **analoghuman said:**
> I'm having a similar problem. A shell script set to autolaunch at startup through Startup Applications where xset isn't sticking.

I know it's running since the script also runs a series of xmodmap commands and those changes work fine. It's just that none of the xset settings work. I've tried adding "sleep 10" but it didn't help. The script is attached.

```
#!/bin/sh

xmodmap -e "remove shift = Shift_R"
xmodmap -e "keycode 62 = Up"
xmodmap -e "keycode 114 = Down"
xmodmap -e "keycode 111 = Shift_R"
xmodmap -e "keycode 116 = Right"
xmodmap -e "keycode 105 = Prior"
xmodmap -e "keycode 115 = Next"
xmodmap -e "keycode 112 = Control_R"
xmodmap -e "keycode 117 = End"
xmodmap -e "add shift = Shift_R"
sleep 10
xset r
xset r 62
xset r 105
xset -r 111
#xset r rate 400 40
```
The changes made by "xset" are "persistent" (the function doesn't end when the script does), so they *may* need their own script.

But in general, I've found that Terminal Commands don't need "#!/bin/sh" at the top (this may vary based upon where you save your script) if you don't precede your commands with "exec".

And make sure you made the script "executable" first by executing the command: sudo chmod a+x /path/to/your/script.sh

---

