---
title: "Script will not run at login, but runs fine manually"
date: 2011-01-13
forum: General Help
---

### Post by jimmy the saint on 2011-01-13
Hey all,

So I have a script that I need to run at login.  I have added it to sessions, but it doesn't work.  I can run it through nautilus, and via a terminal just fine.  This is the script

```
#!/bin/bash
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 40
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 9 3 8 0 1 2 3
```

I have added it to the "session" startups with 
```
/home/me/script.sh
```
and
```
sh -c /home/me/script.sh
```

Neither of them have worked.  I also tried adding it to /etc/rc2.d with no success.

The script IS executable by me.

What am I missing here?

Thanks

---

### Post by tredegar on 2011-01-13
> I have added it to sessions, but it doesn't work.
Do you mean "Startup Applications"?

Scripts I add there do not run unless I put a **sleep 30** as the first command.
Then they run fine.

Ununtu's startup sequence (10.04.1LTS) appears to be, err, "flakey" at the moment.

---

### Post by jimmy the saint on 2011-01-13
Thanks, that did it.  I had tried adding "sleep 10" but that did nothing so I removed it.  I am less impressed with 10* than I was with 8*  

Oh well, thanks for you help man!

---

### Post by ajgreeny on 2011-01-13
You can add the sleep option to a startup command in the Startup Applications with a simple edit of the usual command to ```
bash -c "sleep 10; command"
``` or you could just add the sleep as top line in your shell script, if you prefer to do it that way.

As an example I have to start conky with the addition of the command```
 bash -c "sleep 10; conky"
```for a 10 sec sleep or the conky window is displayed with borders and no transparency.

---

### Post by tredegar on 2011-01-13
@ jimmy the saint
> Thanks, that did it. I had tried adding "sleep 10" but that did nothing so I removed it. I am less impressed with 10* than I was with 8* 

May I take it that the** sleep 30** fixed it?

Ubuntu 8.04 was fine, good and reliable, but support for that desktop is now discontinued :(

The 'buntu developers should realise that startup scripts should not be run until the system has the resources to enable them to run, or they will break.

Meanwhile we have to make "work-arounds", or move to a more stable, and less "cutting edge", distro.

I am ready to move. Perhaps to "it just works" Debian without the pretty bells and whistles.

Best wishes.

---

### Post by hawkmage on 2011-01-13
Many scripts that run at startup do not have much on their path so try using the fully qualified paths to the executable you are running or define the path at the beginning.

---

