---
title: "Computer extremely unresponsive for 5 minutes after login"
date: 2009-08-12
forum: General Help
---

### Post by koma77 on 2009-08-12
After booting up and logging in, my computer is extremely laggy and unresponsive.

This is due to massive disk activity. If I look at what's going on I can see that updatedb is running, and also preload.

I guess updatedb might be the cause. But this has not been that way with earlier releases of Ubuntu! Now it can take a minute or two just to start a web browser while this is going on!

I have a quad core duo CPU with 4 gigs of RAM, so the computer is fast enough alright...

Is this happening for more people? What can I do about it?  (How was it done before?)

---

### Post by Janeway on 2009-08-12
Hi,

you could open a terminal and use top to monitor all processes and their CPU and Memory usage. That might help to find out which process causes this.

Then you could try to disable that process under System -> Preferenies -> Sessions.

Best regards
Janeway

---

### Post by P4man on 2009-08-12
the OP already posted what causes it: updatedb.
It mildly annoying when it runs on my system (which isn't half as powerful as yours), but not nearly as bad as your case. Is it possible you have large NTFS volumes that updatedb scans?

You could try altering its behaviour by editing  /etc/updatedb.conf 
For instance, you could add paths to PRUNEPATHS so it won't index them, when you know it doesn't need to anyway. You could also try disabling updatedb from cron daily, but Im not sure thats a good idea or not.

---

### Post by koma77 on 2009-08-12
Actually I have large NTFS volumes in my computer. But they are not mounted at boot, so that should not be what's hogging up updatedb.

Any more ideas on what could be the problem? I only get this once per day no matter of how many times I boot during a day. I guess that is because of the way updatedb is scheduled to run?

---

### Post by P4man on 2009-08-12
disclaimer: you can try this at your own risk, I never tried it, nor did I see it posted anywhere and I only half know what Im suggesting here :p

updatedb is run daily. The script is:

/etc/cron.daily/mlocate

You could simply try moving it to /etc/con.weekly/

so it runs once a week. Or you could disable it all together, and manually run mlocate now and then

also, copy paste here what other scripts are in cron.daily. Perhaps its something else as well.

---

### Post by P4man on 2009-08-12
btw, I just manually ran the script on my machine, and takes ~40s and while there is plenty of harddisk activity, I can't say I notice any slowdowns. My PC is like half yours lol (dualcore C2D, 2GB ram). Im wondering if we are looking at the right thing here. Try running it manually:

```
sudo /usr/bin/updatedb.mlocate
```

And see if your system bogs down for 5 minutes?

---

### Post by koma77 on 2009-08-12
Good idea!

I ran the script manually and it took about 5 minutes with a lot of disk activity.
However, the system did not feel as slowed down as it does on a first boot of the day!

So I guess that there are several things going on at the same time to cause this.

The contents of /etc/cron.daily/ is:

0anacron
apport
apt
aptitude
bsdmainutils
chkrootkit
find
find.notslocate.dpkg-new
logrotate
man-db
mlocate
ntp
popularity-contest
samba
slocate
standard
sysklogd
sysstat


Is that what you have as well?

---

### Post by P4man on 2009-08-12
> **koma77 said:**
> 
The contents of /etc/cron.daily/ is:

0anacron
apport
apt
aptitude
bsdmainutils
chkrootkit
find
find.notslocate.dpkg-new
logrotate
man-db
mlocate
ntp
popularity-contest
samba
slocate
standard
sysklogd
sysstat


Is that what you have as well?

FWIW I got:

0anacron  apt-cacher-ng  google-chrome  mlocate             samba
apport    aptitude       logrotate      ntp                 standard
apt       bsdmainutils   man-db         popularity-contest  sysklogd


Im not sure what those scripts do that you have and I dont, but you can open them just in a text editor and have a look, google on it, and/or execute them to see how disk intensive they are.

id be particularly interested in: find and find.notslocate.dpkg-new

Did you perhaps upgrade from hardy or gutsy? I think you got several scripts doing the same there. If my memory is correct, those two scripts did the same thing as mlocate in older ubuntu releases. If that turns out to be true, then you can probably ditch them.

---

### Post by koma77 on 2009-08-12
You are right!

Both find and find.notslocate.dpkg-new runs updatedb. As does mlocate!

And yes, I did upgrade hardy to gutsy. (Running jaunty now)

I'll try to ditch the two find-scripts and see if that does it!

Thanks for your ideas: very helpful!

---

### Post by koma77 on 2009-08-13
After booting up this morning I get disk activity, but it is not blocking the computer!

I guess this issue is solved! 
:)

I also removed chkrootkit by the way.

Thanks for helping!

---

