---
title: "Moblock problems- no icon"
date: 2009-12-22
forum: General Help
---

### Post by PDA1 on 2009-12-22
I installed Moblock in my Ubuntu 9.10


the command Sudo moblock status (or whatever it's called) says that Moblock is running.

The only problem is that I have no icon for Moblock and have no listing of it in my applications list at the top left of my screen so I can't control Moblock.

How do I fix this?

---

### Post by lovinglinux on 2009-12-22
It is a command-line application. There is no gui and no icon for it.

To see the status:

```
sudo blockcontrol status
```

Other commands

> From [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)
[LIST]
[B]
[*]blockcontrol start[/B] - inserts iptables rules and starts the IP block daemon. If the blocklist configuration changed, rebuild the master blocklist.
[*]**blockcontrol stop** - deletes iptables rules and stops the IP block daemon.
[*]**blockcontrol restart** - restarts the IP block daemon.
[*]**blockcontrol reload** - rebuilds the master blocklist and reloads the IP block daemon if it is running.
[*]**blockcontrol update** - updates the blocklists, rebuilds the master blocklist and reloads the IP block daemon.
[*]**blockcontrol status** - gives the iptables settings and the status of the IP block daemon.
[*]**blockcontrol test** - does a simple test to check if the IP block daemon is working (pings a random IP in the blocklist and checks if this IP was logged in the block daemons logfile and if it answered).
[*]**search PATTERN** - outputs the occurences of a keyword and the names of the single blocklists.
[*]**stats** - reports MoBlock's statistics
[*]**reset_stats** - resets MoBlock's statistics
[*]**show_config** - shows the current configuration settings.
[/LIST]

If you need a gui, you can install [mobloquer](apt:mobloquer), but it seems it is lacking a maintainer. I don't know if it is working properly, because I don't use it.

For further information see [General Moblock thread](http://ubuntuforums.org/showthread.php?t=803183).

---

### Post by PDA1 on 2009-12-22
How can I add IP's that are allowed?  I'm using Gmail via Thunderbird and Moblock stops it.

I installed **Mobloqer** and it let me add allowed IP's to it.  The only problem was Mobloqer said it wasn't running.

What I want is a simple IP blocker similar to PeerGuardian.

Any advice?


Whoops, so sorry- I just read your comments about Mobloqer.....it's early in the morning.

---

### Post by lovinglinux on 2009-12-22
> **PDA1 said:**
> How can I add IP's that are allowed?  I'm using Gmail via Thunderbird and Moblock stops it.

I installed **Mobloqer** and it let me add allowed IP's to it.  The only problem was Mobloqer said it wasn't running.

What I want is a simple IP blocker similar to PeerGuardian.

Any advice?


Whoops, so sorry- I just read your comments about Mobloqer.....it's early in the morning.


All instructions you need are at [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

Perhaps you will be more comfortable with [iplist](http://iplist.sourceforge.net/), which looks like PeerGuardian.

---

### Post by PDA1 on 2009-12-22
I've really gotta be the dumbest guy on the face of the earth.  Yes, iplist is exactly what I want.  The only problem is I'm just too stupid to know how to install it.  I just wish someone would make this easier 'cause I have no idea how to do it.

Get this....but you got to have that first...so get that and then change that.   Talk about frustrating!

---

### Post by lovinglinux on 2009-12-22
> **PDA1 said:**
> I've really gotta be the dumbest guy on the face of the earth.  Yes, iplist is exactly what I want.  The only problem is I'm just too stupid to know how to install it.  I just wish someone would make this easier 'cause I have no idea how to do it.

Get this....but you got to have that first...so get that and then change that.   Talk about frustrating!

First remove moblock and mobloquer
```
sudo apt-get purge moblock mobloquer
```

Then download one of those files (depending on your system) ending with .deb from [here](http://sourceforge.net/projects/iplist/files/). Double click the downloaded file to install.

I also recommend reading [this](https://help.ubuntu.com/9.10/add-applications/C/index.html).

---

### Post by PDA1 on 2009-12-22
Ok I got IPBlock and it's working.

Thank you for the help.

---

