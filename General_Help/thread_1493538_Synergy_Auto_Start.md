---
title: "Synergy Auto Start"
date: 2010-05-25
forum: General Help
---

### Post by muncherelli on 2010-05-25
So i'm trying to start synergy at gdm start on 10.04.  Basically what I've done is followed the instructions at 

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

The problem is when I actually log into my user account, it locks up my system because the line 

/usr/bin/killall synergyc
while [ $(pgrep -x synergyc) ]; do sleep 0.1; done
/usr/bin/synergyc <SERVER HOSTNAME>

is looking to kill synergyc as my regular user, not as root.  The process is running as root and I need to be able to kill it before firing up synergy as my user account.

Any ideas how to kill the root synergy?  The reason I want it to run as root at the beginning is so I can log in via synergy, then kill that root session and start one under my username.  Make sense?  Thanks!

---

### Post by Brandon Williams on 2010-05-26
By the time you get to 85synergyc, which is the code from the howto that would be running as your user, synergyc should not be running any more. It should have been killed by /etc/gdm/PostLogin/Default already. Are you sure that /etc/gdm/PostLogin/Default is executable and that it is actually running?

One thing that I don't like about the method described in the howto is that, as you note, it will hang login if the kill doesn't work for some reason. I suggest that you do this instead:
```
/usr/bin/killall synergyc
i=0 
while ps -fC synergyc >/dev/null 2>&1 && [ $i -lt 10 ]; do 
    sleep 0.1
    i=$(( i + 1 ))
done
ps -fC synergyc >/dev/null 2>&1 && /usr/bin/synergyc <SERVER HOSTNAME>
```
That way, at least you'll get into the desktop, even if your attempt to start synergyc fails.

---

