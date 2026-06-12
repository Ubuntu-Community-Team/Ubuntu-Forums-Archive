---
title: "Vegastrike sound issue."
date: 2011-05-28
forum: General Help
---

### Post by elitejarod on 2011-05-28
Alright, so I recently got Vegastrike working after some toils with XTERM not loading.

Now I purposefully changed the resolution too high so that the game would error out so that I could show you the sound bug.

I do know that if I lower my resolution it will function, but I get no sound, no music, not even system beeps.

I believe it's tied to one line of code, but being a total newb in linux I haven't figured out what I need to do to fix it.

See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for license details.

```
GOT SUBDIR ARG = 
Found data in ..
Using /home/jarod/Downloads/vegastrike-0.5.0 as data directory
Using .vegastrike-0.5.0 as the home directory
Found MODDIR = /home/jarod/Downloads/vegastrike-0.5.0/mods
USING HOMEDIR : /home/jarod/.vegastrike-0.5.0 As the home directory 
CONFIGFILE - Found a config file in home directory, using : /home/jarod/.vegastrike-0.5.0/vegastrike.config
DATADIR - No datadir specified in config file, using ; /home/jarod/Downloads/vegastrike-0.5.0
SIMULATION_ATOM: 0.05
MISSION_NAME is empty using : main_menu.mission
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
running import sys
print sys.path
sys.path = [r"/home/jarod/Downloads/vegastrike-0.5.0/modules/builtin",r"/home/jarod/Downloads/vegastrike-0.5.0/modules",r"/home/jarod/Downloads/vegastrike-0.5.0/bases"]
['/usr/local/lib/python24.zip', '/usr/local/lib/python2.4/', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/local/lib/lib-dynload']
testing VS randomrunning import sys
print sys.path
['/home/jarod/Downloads/vegastrike-0.5.0/modules/builtin', '/home/jarod/Downloads/vegastrike-0.5.0/modules', '/home/jarod/Downloads/vegastrike-0.5.0/bases']
**open /dev/[sound/]dsp: No such file or directory**
**open /dev/[sound/]dsp: No such file or directory**
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x15a
  Serial number of failed request:  122
  Current serial number in output stream:  124
```Bolded part above isn't finding sound.  But in Ubuntu desktop and other games I've downloaded I do have sound, full use of it.

I found somewhere that it was saying I had the wrong sound card when I have a realtek on my motherboard and it asked me to edit a file in the root directory, which I did, however it doesn't seem to help the issue.

I'm totally stumped as to what the hell I need to do to get sound.  Game looks amazing, but with no sound it's sorta worthless right at the moment.

Any help would be appreciated.

---

### Post by elitejarod on 2011-05-29
Nobody?  Not one of you has any idea what the issue is with my sound card?

---

### Post by elitejarod on 2011-05-30
not sure if this is against the rules, but BUMP, someone throw me a bone?

---

### Post by DieEier on 2012-02-28
Hi there. I know this thread is very old and I may not be the best person to help you but here goes.

Vegastrike seems to be looking for your sound device in the wrong dir. (see below.) I suspect the line should read something like open /dev/snd/ .

Try looking at the config files for Vegastrike and find a line that says /dev/[sound/]  or similiar and change that to /dev/snd.

I just started wrestling with my own Vegastrike sound problems so would appreciate it of you let me know if you've found a solution.

Good hunting.
Die Eier
:P

**open /dev/[sound/]dsp: No such file or directory** **open /dev/[sound/]dsp: No such file or directory**

---

### Post by Astaedus on 2012-03-23
try installing alsa-oss
```
sudo apt-get install alsa-oss
```

then run vegastrike like this:
```
aoss vegastrike
```

---

