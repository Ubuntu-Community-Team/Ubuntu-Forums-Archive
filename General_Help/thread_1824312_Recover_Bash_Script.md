---
title: "Recover Bash Script"
date: 2011-08-13
forum: General Help
---

### Post by OldManRiver on 2011-08-13
All,

Is there a way to determine the time of last reboot and open all sessions and/or files that were open with a BASH script?

Oh also on this topic, does anyone know where a good repository of BASH, PERL and other Linux System Scripts are?

Thanks!

OMR

---

### Post by idoitprone on 2011-08-13
> **OldManRiver said:**
> All,

Is there a way to determine the time of last reboot and open all sessions and/or files that were open with a BASH script?

Oh also on this topic, does anyone know where a good repository of BASH, PERL and other Linux System Scripts are?

Thanks!

OMR

I do not know a bash script on how to do it, but I can tell you how to find some them

Look at /var/log
It contains all the logs of you system, but I am not sure about how to file opening

```
kernel.log
```kernel errors or boot time stuff. Things that appear when you boot

```
auth.log
```everytime you use sudo, su, loggins or logouts

```
syslog.log
```reboot/ shutdown/ suspend and etc

In you home directory,
```
.bash_history
``` will tell you what commands you did

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/var.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/var.html)

btw, system scripts vary distro. I using arch right now, so it is at /etc/rc.d/ 

[http://upstart.ubuntu.com/wiki/](http://upstart.ubuntu.com/wiki/)

Ubuntu uses upstart
[http://upstart.ubuntu.com/wiki/](http://upstart.ubuntu.com/wiki/)
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
I cannot find the simple documentation on messing around with system services, but I guess this will do

Rant: Why wont Ubuntu get rid of upstart or maybe they afraid lennery pottery will break their system just like how the sound was gone.

---

### Post by OldManRiver on 2011-08-14
idoitprone,

Thanks for the info, to look at logs I usually use:

tail -n xxx /mypath/mylogfile > sometextfile.txt

or could use:

cat /mypath/mylogfile | grep searchstring > sometextfile.txt

or something like that to get those details.  I'll experiment with these and see what I get.  Will put the code up here and progress it as I go.

As far as the distro thing, you would think Ubuntu would stay consistant on where they keep things, but since they only overlay the debian kernal, if debian makes a change in locals, then that is by default forced upon us here in the Ubuntu community.  So far Debian has been pretty consistent with only minor changes, for which I'm thankful, there are other distros out there that seem to change a lot more.

Anyway this is not a main focus, so may not get on this right away, but I will over time.

Again thanks for the info!

Cheers!

OMR

---

### Post by Doug S on 2011-08-14
For this:```
cat /mypath/mylogfile | grep searchstring > sometextfile.txt
```
This will work also:```
grep searchstring /mypath/mylogfile > sometextfile.txt
```
or, to include spaces in the search string:```
grep "search string" /mypath/mylogfile > sometextfile.txt
```

---

### Post by OldManRiver on 2011-09-28
All,

So I need a loop to look at all the log files to really determine what I need?

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #22 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

