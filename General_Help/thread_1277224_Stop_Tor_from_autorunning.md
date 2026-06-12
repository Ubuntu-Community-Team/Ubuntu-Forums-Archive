---
title: "Stop Tor from autorunning"
date: 2009-09-28
forum: General Help
---

### Post by T.R. on 2009-09-28
This isn't so much a problem as an annoyance: Tor autoruns when I start up my machine, and Privoxy can't control Tor if it's already running.

I've been able to work around this by using ```
sudo killall tor
``` in the terminal, but that's a temporary fix. I want to set it so Tor doesn't start a process until Vidalia tells it to.
I've read about sysv-rc-conf and from what I gather I think it can help me get what I want. However, I don't understand what the runlevels mean. (When I run sysv-rc-conf Tor is checked on levels 2 3 4 and 5.) Could someone help me figure out how to do this through sysv-rc-conf, or tell me another way to disable autorun on startup for Tor?

tl;dr I want Tor to only run when I tell it to, through Vidalia.

---

### Post by bruno9779 on 2009-09-28
why don't you make a script like this:

```
#!/bin/bash

killall tor
```

save it and make it run at startup in preferences.

(I don't usually sudo the command killall, but it depends on the circumstances)

surely there is a better way, this is just a workaround

---

### Post by Soul-Sing on 2009-09-28
T.R. runs TOR in a relay? You can easily stop this via Vidalia.

---

### Post by T.R. on 2009-09-28
I'm not running it in a relay. It just runs on its own at startup.

---

### Post by T.R. on 2009-09-28
bruno: I tried the script it didn't seem to work. I think Tor might autorun just after startup, or it's lower priority than the autorun script.

It also seems I have to sudo killall with Tor. If I don't bash gives me an Operation not permitted message. I'll try adding sudo to the script to see if that changes anything.

Edit: adding sudo to the script didn't make it work.

If I can figure out sysv-rc-conf I could probably keep it from running at startup to begin with...

---

### Post by bruno9779 on 2009-09-28
I am going to try and install tor tonite, to see where it ends up.

You could also check if it is from the services menu that you control it's behavior

---

### Post by T.R. on 2009-10-28
Bootup manager (bum) fixed it.

---

### Post by exploding loaf of bread on 2009-11-01
How did you manage to do that with bum?

 I have been trying to do the same thing for the last 3 days with no success. I managed to stop tor from starting on startup with bum but then when Vidalia starts it gives me the error message "[Warning] If you set the "User" option, you must start Tor as root.".

---

### Post by T.R. on 2009-11-25
I just unchecked the box for Tor, and it worked.

EDIT: if bum isn't working, type
```
sudo sysv-rc-conf
```
in terminal, go down to tor, and toggle off all the runlevels for tor.

---

### Post by anonSam on 2009-11-25
This command always removes TOR from the start-up for me:

```
sudo update-rc.d -f tor remove
```


But also note that when TOR updates to a new version it does re-add its self to the start-up and I have to run the command again.

It's really too bad this is TORs default setting. I think it should be the other way around.


For Privoxy:

```
sudo update-rc.d -f privoxy remove
```

---

### Post by T.R. on 2009-11-25
On my machine Privoxy is set to autorun and it works fine. It might just be the settings and packages on my machine, but I don't think it matters except for maybe a slightly better boot time with it off.

---

### Post by rifter on 2010-04-07
> **leoquant said:**
> T.R. runs TOR in a relay? You can easily stop this via Vidalia.

Vidalia cannot stop or otherwise control TOR unless it started it.  And of course it can't start it if it is already started. It's kind of annoying.

---

### Post by rifter on 2010-04-07
> **anonSam said:**
> This command always removes TOR from the start-up for me:

```
sudo update-rc.d -f tor remove
```


But also note that when TOR updates to a new version it does re-add its self to the start-up and I have to run the command again.

It's really too bad this is TORs default setting. I think it should be the other way around.


For Privoxy:

```
sudo update-rc.d -f privoxy remove
```

Or at the very least, if you install Vidalia Tor should get removed from startup. Or the Vidalia people should figure out what magic is required to control an already running Tor or restart it through their GUI.

---

### Post by rifter on 2010-04-07
> **anonSam said:**
> This command always removes TOR from the start-up for me:

```
sudo update-rc.d -f tor remove
```


But also note that when TOR updates to a new version it does re-add its self to the start-up and I have to run the command again.

It's really too bad this is TORs default setting. I think it should be the other way around.


For Privoxy:

```
sudo update-rc.d -f privoxy remove
```

I read the manpage for update-rc.d .. what it does is manipulate the links under /etc/rc0.d .. if you do remove it deletes the links, but that means that when you upgrade the package again the links will get put back.  What you need to do is change the S in front of the link name to a K.  update-rc.d will do this for you if you do "disable" instead of remove, and the next time you upgrade update-rc.d will see there are links there and leave that alone.

```

$ sudo update-rc.d tor disable
update-rc.d: warning: tor start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: tor stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
 Disabling system startup links for /etc/init.d/tor ...
 Removing any system startup links for /etc/init.d/tor ...
   /etc/rc0.d/K20tor
   /etc/rc1.d/K20tor
   /etc/rc2.d/S20tor
   /etc/rc3.d/S20tor
   /etc/rc4.d/S20tor
   /etc/rc5.d/S20tor
   /etc/rc6.d/K20tor
 Adding system startup for /etc/init.d/tor ...
   /etc/rc0.d/K20tor -> ../init.d/tor
   /etc/rc1.d/K20tor -> ../init.d/tor
   /etc/rc6.d/K20tor -> ../init.d/tor
   /etc/rc2.d/K80tor -> ../init.d/tor
   /etc/rc3.d/K80tor -> ../init.d/tor
   /etc/rc4.d/K80tor -> ../init.d/tor
   /etc/rc5.d/K80tor -> ../init.d/tor

```

---

### Post by swati123 on 2010-04-07
thanks for this info.

regards
Swastik bhargava
Excel combines
MeritVCO extra virgin coconut oil

---

### Post by rifter on 2010-04-07
> **rifter said:**
> Vidalia cannot stop or otherwise control TOR unless it started it.  And of course it can't start it if it is already started. It's kind of annoying.

I stand corrected.  The Vidalia teem have figured out the magic after all, and _[color=blue][given instructions!](https://trac.vidalia-project.net/wiki/FAQ#ExistingTor)[/color]_.  So you could also edit your torrc apparently and fix this.  It's weird though because I could have sworn my tor was already configured to use that control port.  Incidentally I found that while reading about _[color=blue][this bug](https://bugs.launchpad.net/ubuntu/+bug/110666)[/color]_ in my quest to find a fix for Vidalia's recent propensity to freeze up on my system.

---

### Post by rifter on 2010-04-13
I decided to get rid of Vidalia.  It was hogging resources, going greyed out all the time, and in the end the only thing it was "controlling" about tor was starting and stopping it.  so I just got rid of Vidalia and set tor back to starting on startup; no problems anymore.

---

### Post by Telsyii on 2010-10-06
I dont under stand any of this script talk. can someone tell me where and how to open up where the script goes. and what the exact script is?

---

### Post by 101011010010 on 2010-10-06
Hello. 
What is being said, is that if you enter> sudo update-rc.d tor disable[FONT=Verdana]
into a terminal, Tor will stop running at start up & updates won't affect the change.
(Click on Applications/Accessories/Terminal. Copy & paste the command into it. Type in your password (you wo'nt see it), press Enter & done.) I did the same for Polipo as well.
I hope this helps.
P.S. 1. Don't worry about the script talk, the above method works, so no need.
2. Thanks "[/FONT]rifter" for the solution.:)

---

### Post by technophant on 2012-04-18
FYI, to check on Tor service status use
```
/etc/init.d/tor status
```other possible commands are ```

/etc/init.d/tor start
/etc/init.d/tor stop
/etc/init.d/tor restart
/etc/init.d/tor reload
/etc/init.d/tor force-reload
```

also, I would suggest to Tor developers to add the commands:
/etc/init.d/tor autostart-on
and
/etc/init.d/tor autostart-off
to make the process of managing the service easier.
*Note: the last two commands are not actual commands*

---

### Post by oldos2er on 2012-04-18
Closed. Please don't bump old threads.

---

