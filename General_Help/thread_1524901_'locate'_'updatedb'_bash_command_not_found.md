---
title: "'locate' 'updatedb' bash: command not found"
date: 2010-07-05
forum: General Help
---

### Post by NT4usB on 2010-07-05
I recently installed 10.04, in the process of installing MythTV...
I'm looking for installed files and find bash no longer finds updatedb or locate commands.
I did change /etc/hosts and /etc/hostname to change the name of the box. Could this have hosed those commands?
I tried them as root... sudo -i, same result...

---

### Post by fragos on 2010-07-06
mlocate is the package you may want, it's a newer version locate. It would be installed with an Ubuntu Live CD install.

---

### Post by NT4usB on 2010-07-06
Thanks for that. I've heard around that locate is no longer installed by default but I don't think that's all the problem... unless half the Linux commands I use are no longer installed by default.
dmesg, grep, and who knows what else doesn't work anymore.
Me thinks my bash is borken.

ED: hmmm... got me thinking. This install went bad from the start. First go round, everything installed perfectly. Then, thanks to the new drive monitor software, I see I installed on a drive that had ~ 3 years uptime already. Not the best choice for a MythTV PVR.
Dug another drive out of the closet and the installer wouldn't run at all. Same CD, same everything...
I installed a kernel then installed everything else via command line from the repositories.
Probably a bunch of key stuff didn't get installed...

---

### Post by WorMzy on 2010-07-06
That sounds very suspect, can you run 'echo $PATH' and post the output here?

If that command doesn't work, then there's definitely something wrong with your PATH variable. If so, post the contents of ~/.bash_profile and/or ~/.bashrc here instead (open them with gedit, rather than trying to use cat. :p)

---

### Post by NT4usB on 2010-07-07
$PATH looks ok. 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Installed (m?)locate and now updatedb works... and locate.
(wtf it was removed in the first place is beyond me... find is useless)
I haven't found any commands tonight that bash pukes. Maybe it's healed itself, maybe I'm typing better... maybe I'm just getting used to the screwy new ways 10.04 does the same old things...

Anyway, I'm marking this solved. Thanks for help!
Off to find out why it hangs on boot, and various other niggles.

---

### Post by td8f4 on 2010-11-03
I have this problem too, but i still can't install updatedb or locate.
i'm under ubuntu 10.10

i've tried installing; sudo apt-get install ...
slocate
dlocate
locate
updatedb
And reinsalling findutils
when i try to install mlocate, it says
"Package mlocate not available, but is referred to by another package."

any ideas on other package names??
thanks

---

### Post by fragos on 2010-11-03
I wonder if some of your "locate"s are interfering with each other. slocate for example is an old version. I'd remove them all and only install mlocate which is the latest of the locate series. Works great for me on 10.10. I installed mlocate with Synaptic from the standard repositories. Updatedb is part of mlocate. Slocate isn't in the 10.10 repositories and dlocate has something to do with dpkg and I believe only finds deb packages on your system.

---

### Post by pterosky on 2011-12-14
Thanks guys, sudo apt-get install mlocate got me updatedb :-)

---

