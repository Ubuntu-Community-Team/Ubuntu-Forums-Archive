---
title: "Problem to shutdown (X server)"
date: 2012-03-06
forum: General Help
---

### Post by kamelie1706 on 2012-03-06
Hi,

I have regular challenge to shutdown from Kubuntu.

It happens after the alsa service is closed. If I connect to a terminal I can "sudo shutdown 0" and it works.

I have attached screenshot and my xsession-error file before the shutdown. 

Any hint is appreciated.

Thanks

---

### Post by _0R10N on 2012-03-06
Sorry, I'm not really into kubuntu, but when does this happen? when shutting down from the menu? Have you tried executing
```
sudo init 0
```
just to see whether it shuts down right=.

---

### Post by kamelie1706 on 2012-03-06
no issue with your command.

"sudo shutdown 0" is also working.

Sometimes even if I shutdown it starts a disk check ....

---

### Post by kamelie1706 on 2012-03-07
I got some extra lead. The actual line that first fail seems to be:
```
mountall disconnected from Plymouth [fail]
check syslog for diagnostic
```In syslog file I find
Mar  8 03:30:20 htpc kernel: [  470.437858] nepomukservices[2301]: segfault at 0 ip   (null) sp bfcd6d6c error 14 in nepomukservicestub[8048000+6000]
Mar  8 03:30:23 htpc kernel: [  473.652072] tty_ldisc_hangup: waiting (Xorg) for tty7 took too long, but we keep waiting...

Since I have network mounted directory I have tried
[http://trl.ca/2011/10/kubuntu-oneiric-wont-shut-down-anymore/](http://trl.ca/2011/10/kubuntu-oneiric-wont-shut-down-anymore/)
and
[http://askubuntu.com/questions/43016/kubuntu-hangs-on-shutdown](http://askubuntu.com/questions/43016/kubuntu-hangs-on-shutdown)

but none of them worked ....

I tried to kill all nepomuk related processes
/usr/bin/akonadi_nepomuk_feeder --identifier akonadi_nepomuk_feeder
/usr/bin/nepomukcontroller -session 1068747063000133079626700000025110008_1331172442_156286
/usr/bin/nepomukserver

did not solve the shutdown

Is there any place in the kde shutdown process I could put 
sudo init 0
to be executed as root without password

Any idea?

ATI driver issue (not using proprietary) ?

---

### Post by kamelie1706 on 2012-03-11
Could it be a conflict between X server and the kernel?

From the kdm.log I can find
*****
X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: **Linux 2.6.24-29**-server i686 Ubuntu
Current Operating System: Linux htpc 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/**vmlinuz-3.0.0-16-generic-pae **root=UUID=fe3c9af4-f074-426e-9bf2-a4c8aa55e372 ro quiet splash vt.handoff=7
Build Date: 19 October 2011  05:09:41AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
*****

I am now lost and no idea in which direction to search ....

---

### Post by kamelie1706 on 2012-03-11
Something that might be important to note:
When I get stuck on the state described on the screenshoot. I open a new terminal and use the command "sudo init 0" or "sudo shutdown 0" and then only I see:
- some console messages
- kubuntu splash screen

I do not see splash screen before seen the message shown on the screenshot ...

Not being familiar with ubuntu shutdown process I have no clue if it helps!

---

### Post by kamelie1706 on 2012-03-18
Should I wait for fresh install on next kubuntu release ???

---

### Post by kamelie1706 on 2012-04-15
Now it is randomly being able to shutdown ... when blocked it seems the last service that get stuck is "Start Alsa Timidity" or something similar.

Anyone as it is very ugly to turnoff computer with "poweroff" button ....

---

