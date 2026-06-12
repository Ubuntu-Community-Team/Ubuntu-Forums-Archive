---
title: "desktopcouch-se is eating up my cpu"
date: 2010-03-30
forum: General Help
---

### Post by Endomancer on 2010-03-30
Yesterday I installed Lucid Beta 1 and it was all running beautifully, could even use desktop effects and still run things at full screen without the screen going blank black (couldn't with Karmic). So I was very impressed.

This morning however, I decided to run the update manager to see what updates there were and found 448 of them which took about 3.5hrs to download. 

After the updates I rebooted the computer and watched the cpu graph in conky top out in a matter of seconds and the culprit I found is desktopcouch-se which has been taking up all available processor usage.
I had previously never encountered descktopcouch-se or even know of it's existence before this morning, so I'm hoping someone could explain to me what it is/does and hopefully explain how to stop it eating up all the available cpu


Thanx in advance
Endo

---

### Post by tiger2wander on 2010-03-31
Me too, but after upgraded many packages today it's seen get more good when done see the desktopcouch service on top `top` :)

---

### Post by Mark Phelps on 2010-03-31
Since Lucid is still in beta, the proper forum to post your questions is Development & Programming, Lucid Lynx Testing, not here.

I will be asking the Mods to move this thread there.  Look there for future responses.

---

### Post by edvar on 2011-05-20
I'm having the exact same problem with Natty:

top - 14:29:48 up 37 min,  2 users,  load average: 1.29, 1.14, 1.07
Tasks: 229 total,   2 running, 225 sleeping,   0 stopped,   2 zombie
Cpu(s): 25.4%us,  4.2%sy,  0.1%ni, 69.4%id,  0.1%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   3357112k total,  1695940k used,  1661172k free,    64512k buffers
Swap:  7823616k total,        0k used,  7823616k free,   818208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3205 ed        20   0 19192  12m 4060 R  100  0.4   1:52.04 desktopcouch-se


Any ideas?

It's been happening since I upgraded to the latest kernel 2.26.38-9. I had to upgraded to the unreleased kernel 2.26.39 to fix this: [http://ubuntuforums.org/showthread.php?t=1762949](http://ubuntuforums.org/showthread.php?t=1762949) . However I'm still having the same issue with desktopcouch-se.

---

### Post by edvar on 2011-05-22
It seems to be related to UbuntuOne: [https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/774295](https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/774295)

And by the looks of ~/.cache/desktop-couch/log/desktop-couch-replication.log, it might be it :


2011-05-23 10:44:34,305 WARNING  Can't reach service ubuntuone.  No access token.
2011-05-23 10:44:34,305 DEBUG    finished replicating
2011-05-23 10:44:34,306 DEBUG    starting replicator main loop
2011-05-23 10:46:22,009 DEBUG    started replicating
2011-05-23 10:46:22,022 DEBUG    replication of discovered hosts finished
2011-05-23 10:46:22,036 DEBUG    static pairings are [('9fad4059-4a49-445a-86f3-81a7c025b7d2', 'ubuntuone', True, True)]
2011-05-23 10:46:22,036 DEBUG    Looking up prefix for service 'ubuntuone'
2011-05-23 10:46:22,036 DEBUG    Looking up prefix for service 'ubuntuone'
2011-05-23 10:46:22,036 ERROR    Could not get access token from sso.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Did you upgrade or is this a fresh installation of Ubuntu?

---

### Post by edvar on 2011-05-22
It's a clean fresh install of Natty from early May/2011:

uname -a
Linux ed-linux 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 17:41:08 UTC 2011 i686 i686 i386 GNU/Linux

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

---

### Post by linuxinstalledfromhdd on 2011-05-22
Does this happen when you boot with a freshly made USB stick of Ubuntu 11.04 running?

---

### Post by edvar on 2011-05-22
I don't have a USB stick with Ubuntu. This is a desktop and I used a CD to install Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Because I was going to suggest that you try leaving a "persistent" usb ubuntu live in the unit overnight booted and running, and check the logs in the morning to see if you can replicate the issue.

---

### Post by edvar on 2011-05-22
Can't do that... I have some stuff running on it including apache and it needs to be up most times. An occasional reboot is not a problem but can't leave it unavailable for long periods of time

---

### Post by linuxinstalledfromhdd on 2011-05-22
Begin uninstalling any unneeded applications.. Thin down the system.  Did you remove Ubuntu One yet?  If you do this slowly enough over a period of time you will probably find the cause.  Keep a good eye on the log for any changes. And rechecking what you have already checked.

---

### Post by edvar on 2011-05-22
Just uninstalled everything related to ubuntuone including desktopcouch-ubuntuone, python-ubuntuone and ubuntuone-client and rebooted.

The CPU utilisation is now back to normal. I guess it confirms UbuntuOne as the culprit.

It just sucks not being able to have some sort of proper file/folder sync service out of the box. I guess I'll have to install dropbox instead...

---

### Post by linuxinstalledfromhdd on 2011-05-22
Oh there are plenty of alternative for now, until they can get that problem resolved. I would suggest Dropbox, or maybe spideroak.com ..   Same size for free.  Eventually you will find one that doesn't cause this kind of behaviour with your system hopefully in the interim.

---

### Post by edvar on 2011-05-24
Reinstalled Ubuntu One and this time I noticed desktopcouch-ubuntuone is not installed. Haven't had any CPU issues since.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Good job. I think you found the bug.

---

### Post by samee.zahur on 2011-06-16
Thanks, this post just saved my day! Just got rid of Ubuntu one stuffs, and cpu usage is down again.

Something else got fixed as well, which is weird: my weather indicator (Unity, on Natty) on the top panel became invisible a few weeks back for no apparent reason. Once I got rid of Ubuntu one, the weather indicator reappeared. I didn't do anything else here ... can't be related can it?

---

