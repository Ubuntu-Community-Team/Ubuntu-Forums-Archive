---
title: "tried many ways of killing a process"
date: 2010-11-07
forum: General Help
---

### Post by tobytoby on 2010-11-07
I have spent a few hours now googling, but w/o success. What I want to do is to kill the vlc instance I started in the script (after the files in folder1 have been played). So how do i retrieve that specific pid? I have tried multiple ways of doing it (below is one of them).

#!/bin/bash

vlcfile=/home/user1/Desktop/folder1
vlcvolume=350

vlccommand="/usr/bin/vlc ${vlcfile} --volume ${vlcvolume}"
export DISPLAY=:0.0
$vlccommand
vlcpid=`pidof vlc`
kill $vlcpid

exit 0

---

### Post by sikander3786 on 2010-11-07
You can give htop a try.

```
sudo apt-get install htop
```

```
htop
```

---

### Post by tobytoby on 2010-11-07
I need to kill the process through a script.

---

### Post by The Cog on 2010-11-07
**killall vlc** will probably do the trick, provided you only have one instance of vlc running.

---

### Post by efflandt on 2010-11-07
To get the PID you can run it as a coprocesses.  But that is not going to have any clue when the music finishes playing.  It is only going to return when the user closes vlc, in which case, there is nothing to kill.  So under what conditions would you want to kill it?

For more about **coproc** see **man bash**

Example:

```
#!/bin/bash

vlcfile=/home/user1/Desktop/folder1
vlcvolume=350

vlccommand="/usr/bin/vlc ${vlcfile} --volume ${vlcvolume}"
export DISPLAY=:0.0
coproc $vlccommand
# in yellow so you can see it among other output
echo -e "\033[1;33mvlc COPROC_PID: $COPROC_PID\033[0m"
wait $COPROC_PID

exit 0
```

---

### Post by hakermania on 2010-11-07
killall -v vlc should work!

---

### Post by psusi on 2010-11-07
You don't need a coproc, you just need to background it by suffixing it with & and then its pid will be in the $! variable.

---

### Post by tobytoby on 2010-11-08
efflandt, where I am supposed to see the pid number being displayed? I have a terminal window open but I do not see anything there?

I have tried killall -v vlc. It works fine in terminal, but does not work in a script??
Could the reason be the same why I had to use:
vlccommand=/usr/bin/vlc ${vlcfile}

instead of:

vlccommand=vlc

that it is not clear which user the command should be applied for (or something similar..)

What I want it for is that this script starts several times every hour, if I can not kill the processes, I suppose it either looks good or is good for memory management.

However, one good thing is that I actually think I do not need to keep track of which instance of VLC I should kill. I could as well start the script with killall vlc before I then start a new instance of VLC (if only I could get killall to work....)

---

### Post by bouncingwilf on 2010-11-08
Perhaps you could get the pid using ps

e.g. ps -C vic -o pid=

or something along those lines - sorry I can't give you the exact command but its been over 20 years!


Bouncingwilf

---

### Post by psusi on 2010-11-08
Killall does not work because it is not being run until AFTER vlc is already dead.  You need to background it like I said before.

---

### Post by tobytoby on 2010-11-08
ok, I am giving it another shot. I started a background process and saved the pid in a file. I have then (tried at least) to read the pidnumber from the file at the start of the script (since the script will start many times, the intention is to kill the previous process). What do you think of this (stupid question since it does not work....but I am perhaps on the right track,or?)

```
#!/bin/bash

value="/home/user1/Desktop/testfil2"
echo $value
kill $pidnumber

vlcfile=/home/user1/Desktop/5
spotvolume=200

vlccommand="/usr/bin/vlc ${vlcfile} --volume ${spotvolume}"
export DISPLAY=:0.0

$vlccommand &
pidnumber=$!

savefile="/home/user1/Desktop/testfil2"
echo pidnumber=$pidnumber > $savefile
```

---

### Post by psusi on 2010-11-08
You forgot the part where you load pidnumber from the file.

---

### Post by SeijiSensei on 2010-11-08
You can also use "pidof vlc" to get its process ID.  If you want to use it in a script, save it as an enviroment variable:

```
VLC_PID=$(pidof vlc)
```

---

### Post by psusi on 2010-11-08
Except that gets everything running with "vlc" in the name, which may end up picking up things you don't want.

---

### Post by tobytoby on 2010-11-08
great advice. thanks!

---

