---
title: "Problem removeing &quot;RADclock&quot;"
date: 2010-07-09
forum: General Help
---

### Post by solitaire on 2010-07-09
I installed a program called [ RADclock ](http://www.cubinlab.ee.unimelb.edu.au/radclock/)

It needed certain kernel to run 2.6.28 and i could not get things working.

I've tried to remove the program (It was installed using a *.dep file) but when I try to remove it I get the following error:
```

bill@laptop:~/Downloads$ sudo apt-get purge radclock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  radclock*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 356kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 197818 files and directories currently installed.)
Removing radclock ...
Stopping the radclock daemon: invoke-rc.d: initscript radclock, action "stop" failed.
dpkg: error processing radclock (--purge):
 subprocess installed pre-removal script returned error exit status 1
update-rc.d: warning: radclock start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: radclock stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
Starting the radclock daemon: done.
Errors were encountered while processing:
 radclock
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone got any ideas on how to remove it?

Think I need to do a wipe and reinstall of this laptop anyway...

---

### Post by cariboo on 2010-07-09
Can you stop the service first, and then reove it?

```
sudo  /etc/init.d/radclock stop
```

---

### Post by solitaire on 2010-07-09
No difference! 
I get the same error messages...

It also seems to be trying to start when the remove fails!

From syslog:
```

Jul  9 21:45:41 laptop radclock [3611]: Info:      RADclock - configuration summary
Jul  9 21:45:41 laptop radclock [3611]: Info:      radclock version     : 0.2.2
Jul  9 21:45:41 laptop radclock [3611]: Info:      Verbose level        : normal
Jul  9 21:45:41 laptop radclock [3611]: Info:      Client sync          : ntp
Jul  9 21:45:41 laptop radclock [3611]: Info:      Server IPC           : on
Jul  9 21:45:41 laptop radclock [3611]: Info:      Server NTP           : on
Jul  9 21:45:41 laptop radclock [3611]: Info:      Adjust system clock  : on
Jul  9 21:45:41 laptop radclock [3611]: Info:      Polling period       : 16
Jul  9 21:45:41 laptop radclock [3611]: Info:      TSLIMIT              : 0.000015000
Jul  9 21:45:41 laptop radclock [3611]: Info:      SKM_SCALE            : 1024.000000000
Jul  9 21:45:41 laptop radclock [3611]: Info:      RateErrBound         : 0.000000500
Jul  9 21:45:41 laptop radclock [3611]: Info:      BestSKMrate          : 0.000000200
Jul  9 21:45:41 laptop radclock [3611]: Info:      offset_ratio         : 6
Jul  9 21:45:41 laptop radclock [3611]: Info:      plocal_quality       : 0.000000800
Jul  9 21:45:41 laptop radclock [3611]: Info:      Using plocal         : on
Jul  9 21:45:41 laptop radclock [3611]: Info:      Initial phat         : 1e-09
Jul  9 21:45:41 laptop radclock [3611]: Info:      Host asymmetry       : 0.000000
Jul  9 21:45:41 laptop radclock [3611]: Info:      Network asymmetry    : 0.000000
Jul  9 21:45:41 laptop radclock [3611]: Info:      Host name            : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      Time server          : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      Interface            : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      pcap sync input      : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      ascii sync input     : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      pcap sync output     : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      ascii sync output    : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      ascii clock output   : 
Jul  9 21:45:41 laptop radclock [3611]: Info:      registered get_vcounter syscall at 295
Jul  9 21:45:41 laptop radclock [3611]: Info:      registered get_vcounter_latency syscall at 296
Jul  9 21:45:41 laptop radclock [3611]: Info:      Kernel support NOT detected
Jul  9 21:45:41 laptop radclock [3611]: ERROR:     No kernel support for the radclock, exiting
Jul  9 21:45:41 laptop radclock [3611]: ERROR:     Could not initialise the RADclock

```

---

### Post by jrid on 2010-07-09
@Solitaire.

apt-get is trying to start and stop the radclock before removing it.

The kernel you are running is apparently not patched to support the radclock. The radclock realises it, and exits. The stop action has then nothing to stop, the script exits with an error and apt-get refuses to remove the package.

That's for the diagnosis. Now you have several solutions.
If you want to confirm I got it right, edit your /etc/init.d/radclock file and comment out the start-stop-daemon lines. The script will exit without error which should solve the problem.

Alternatively, use dpkg and a combination of --force options. The man page should be explicit enough.

Please let the forum know if that solved your problem. If not, you can always contact me directly, you will find my email at the bottom of this page: [RADclock project]("http://www.cubinlab.ee.unimelb.edu.au/radclock/")

---

### Post by solitaire on 2010-07-09
Many thinks!!

I commented out all the "start-stop-daemon" lines from /etc/init.d/radclock
and ran sudo apt-get purge radclock.

It worked! it's now gone.

---

