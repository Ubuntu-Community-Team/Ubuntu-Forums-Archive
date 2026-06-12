---
title: "bash script conditional programming not working when not run in terminal"
date: 2012-06-19
forum: General Help
---

### Post by HiImTye on 2012-06-19
I'm having issues using bash scripts if they rely on conditional programming to perform tasks, i.e. this works while they are run from inside a terminal but not when I simply choose to 'run' them:

```
if ps -e | grep conky; then
 killall conky
fi
```likewise, when I 'run' this, it spawns each of these processes regardless of whether they are running already or not:
```
#!/bin/bash

# define variables
STARTPULSE=yes         # PulseAudio sound server + .asoundrc_pulsealsa (configuration file that redirects bad programs, such as Flash, to PulseAudio)
STARTMPD=yes        # Music Player Daemon
STARTDELUGE=yes        # Deluge Daemon
STARTGUAKE=yes        # Guake Terminal
STARTMAXIMUS=yes    # Maximus Window Management
STARTGNOMESHELL=yes    # Gnome-Shell loop

# notify us that we are running
echo running startup tasks. variables are:
echo \$STARTPULSE=$STARTPULSE
echo \$STARTMPD=$STARTMPD
echo \$STARTDELUGE=$STARTDELUGE
echo \$STARTGUAKE=$STARTGUAKE
echo \$STARTMAXIMUS=$STARTMAXIMUS
echo \$STARTGNOMESHELL=$STARTGNOMESHELL

# delete files, if they exist and clear our command history
if [ -f $HOME/.bash_history ]; then
 rm $HOME/.bash_history
 history -c
fi
if ls $HOME/Desktop | grep '~'; then
 rm $HOME/Desktop/*~
fi
if [ -d $HOME/.thumbnails/fail ]; then
 rm -R $HOME/.thumbnails/fail
fi

# Start tasks we are set to run
if [ "$STARTPULSE" = "yes" ]; then
 if [ -f $HOME/Launchers/.startupTasks-soundSystem.sh ]; then
   $HOME/Launchers/.startupTasks-soundSystem.sh pulse 1
 fi
fi
if [ "$STARTDELUGE" = "yes" ]; then
 if ! ps -e | grep deluged; then
   deluged
 fi
fi
if [ "$STARTGUAKE" = "yes" ]; then
 if ! ps -ef | grep guake | grep -v grep; then
   guake &
 fi
fi
if [ "$STARTMAXIMUS" = "yes" ]; then
 if ! ps -e | grep maximus; then
   maximus &
 fi
fi
if [ "$STARTGNOMESHELL" = "yes" ]; then
 if [ -f $HOME/Launchers/.startupTasks-gnomeShell.sh ]; then
   if ! ps -ef | grep $HOME/Launchers/.startupTasks-gnomeShell.sh | grep -v grep; then
     $HOME/Launchers/.startupTasks-gnomeShell.sh &
   fi
 fi
fi

# sleep to give PulseAudio a chance to load before we start loading things that depend on it being loaded
sleep 5

# continue starting tasks
if [ "$STARTMPD" = "yes" ]; then
 if ! ps -e | grep mpd; then
   mpd
 fi
 if ! ps -e | grep mpdscribble; then
   mpdscribble
 fi
fi

sleep 4
echo finished startup tasks
exit
```if, however, I run this inside a terminal rather than choosing 'run' when I choose to 'open' the script file, it runs as expected. any ideas?
(note: this is all from my [conky setup]("http://ubuntuforums.org/showthread.php?t=1960742"))

---

### Post by spikoley on 2012-06-20
Maybe the file isn't set to be executable.  Right click on the file and go to the permission's tab to make it executable.  Or use *ls -la*  to check the permissions and *chmod*  to change them.

---

### Post by HiImTye on 2012-06-20
theyre set, they run, the conditionals are simply ignored and they either launch the processes anyway (in that large bash file) creating multiple instances or they don't 'killall conky'

functions as expected when run in a terminal or called within a terminal

---

### Post by HiImTye on 2012-06-22
bump, no ideas?

---

### Post by papibe on 2012-06-22
Hi HiImTye.

I tested this structure:
```
#!/bin/bash
if ps -e | grep myprocess; then
    killall myprocess
fi
```
and it does works for me here. Both from the terminal, and when double click and 'Run' from the GUI.

Is there's more information you can give us?

Regards.

---

### Post by HiImTye on 2012-06-23
I'm not really sure what else to add. it works properly when called from a terminal or when run inside a terminal (via 'run in terminal'). it worked perfectly before I upgraded to 12.04. my bash scripts all contain bangs so it shouldn't be an issue of one shell vs. another shell (i.e. sh vs. bash).

Ill try it in Unity and see if maybe its a regression in GS

p.s. some processes require the full command output to find (such as some long bash names) in which case you would need to use a structure like this:
```
if (!) ps -ef | grep long_processname_or_full_path | grep -v grep; then
     action
fi
```update:
very strange. I switched to Unity then Gnome-fallback with and whithout effects and back to GS and while it worked perfectly in the others, now it is working perfectly in GS. I'll try again tomorrow once things have been running uninterrupted for a while again and then post again whether or not it has stayed fixed.

---

### Post by HiImTye on 2012-06-23
it's working now. maybe fixed by a package update that never got fully applied until I switched to Unity. who knows.

---

