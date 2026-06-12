---
title: "smartd/hddtemp locks up server, but only after large netatalk activity"
date: 2011-12-04
forum: General Help
---

### Post by bvz on 2011-12-04
Ok, this is a weird one (and it is repeatable).

I have server 11.10 installed (intel d510mo motherboard, Roswell 4-port RIAD card but not using it for anything other than its ports, 1 ssd, 4 Western Digital Green 1TB drives)

I have mdadm running a 4 disk raid 5 array (sdb-sde).

I have installed smartmontools.

I have installed hddtemp (and it is being called in a script by cron as root every 15 minutes)

I have installed Netatalk and Avahi.


The server runs fine for days and days, letting me ssh in and so on.  But as I am still setting it up, I have not really been using Netatalk at all, just ssh.



Then I do a large file operation via the Finder on my Mac.  Last time it was trying to copy 250 Gigs of data to the server.  This time it was deleting 250 Gigs of data on the server.  Each time the result is the same: the copy or delete runs nearly to 100% and then the server freezes.


After that, my troubles begin.  The server will not boot if I have all four drives plugged into the array.  Any other combination (any three, any two, or any single drive) boots fine (of course I have to tell it to skip trying to mount /dev/md0).  If I have all four drives plugged in, it hangs when it gets to launching smartd.  I cannot ping it, I cannot ssh into it.

If I turn off smartd, it will boot properly with all four drive plugged in.

But running hddtemp will cause it to lock up (but intermittently).  If I type the following repeatedly the machine will lock up (in fact, I do this from an ssh session, but I can see the cursor on the actual console freeze - aka stop blinking):

sudo hddtemp /dev/sdb

If I run the previous command in quick succession (using the up arrow and enter), it will lock the entire system sooner or later (usually within 6 or 7 tries).  It does not matter which disk I query (sdb, sdc, sdd, sde).  I can also round-robbin it (check sdb, then sdc, then sdd, then sde, then back to sdb etc.) with the same result (i.e. I don't have to just be hitting the same disk over and over).  Running a script that checks each of the drives sequentially will immediately lock the system every time (maybe because they are running to close together?)

using apt to remove smartmontools does not solve the hddtemp issue (but obviously the system still boots).

Reinstalling smartmontools and then running the following commands also results in a freeze:

```
[~]: sudo smartctl -s on -o on -S on /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.
SMART Attribute Autosave Enabled.
SMART Automatic Offline Testing Enabled every four hours.

[~]: sudo smartctl -s on -o on -S on /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net
```

And there it froze.

The next time I tried it I got this:

```
[~]: sudo smartctl -s on -o on -S on /dev/sdb
[sudo] password for user: 
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net
```

And there it froze.



I also tried running the following command:

```
sudo smartctl --all /dev/sdb
```

It spit out the information requested and then the system froze again.

I rebooted and ran:

```
sudo smartctl --all /dev/sdc
```

and it froze almost immediately (just after the copyright info from smartmontools)




So... (thanks to anyone who read this far) what do I try next?

Since there does not seem to be a particular disk that is giving me issues I suspect it isn't the actual disks that are causing issues (i.e. I don't think I just have a bad drive in there).

Could it be my Roswell 4-port Raid card?  
Any other ideas?  

I'm kind of lost now.


Edit:
I have uninstalled smartmontools and disabled any scripts that call hddtemp for now.  I started copying (as a test) 550 Gigs of data to the server from the Finder.  I have noticed that, in addition to being agonizingly slow, that the array seems to be rebuilding itself.

```
[/var/log]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[1] sde1[4] sdd1[2] sdb1[0]
      2930280960 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [=>...................]  resync =  6.7% (66301948/976760320) finish=1280.2min speed=11852K/sec
      
unused devices: <none>
```

Why would this be happening?

---

### Post by bvz on 2011-12-04
Here is a transcript from when I tried to test the smart status of my four drives:

```
[~]: sudo smartctl -t short /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Sun Dec  4 11:23:17 2011

Use smartctl -X to abort test.
[~]: sudo smartctl -l selftest /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      70%       170         -
# 2  Extended offline    Completed without error       00%       168         -
# 3  Short offline       Completed without error       00%       132         -
# 4  Short offline       Completed without error       00%       119         -
# 5  Extended offline    Completed without error       00%       106         -
# 6  Short offline       Completed without error       00%        81         -
# 7  Short offline       Completed without error       00%        59         -
# 8  Extended offline    Completed without error       00%        57         -
# 9  Extended offline    Completed without error       00%        44         -
#10  Short offline       Completed without error       00%        41         -
#11  Short offline       Completed without error       00%        41         -

[~]: sudo smartctl -t short /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Sun Dec  4 11:26:21 2011

Use smartctl -X to abort test.
[~]: sudo smartctl -l selftest /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      80%      7101         -
# 2  Short offline       Completed without error       00%      7045         -
# 3  Short offline       Completed without error       00%      7030         -
# 4  Extended offline    Completed without error       00%      7020         -
# 5  Short offline       Completed without error       00%      6993         -
# 6  Short offline       Completed without error       00%      6971         -
# 7  Extended offline    Completed without error       00%      6971         -
# 8  Extended offline    Aborted by host               90%      6963         -
# 9  Extended offline    Completed without error       00%      6958         -
#10  Short offline       Completed without error       00%      6953         -

[~]: sudo smartctl -t short /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Sun Dec  4 11:30:08 2011

Use smartctl -X to abort test.
[~]: sudo smartctl -l selftest /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

```

And there it froze again.  There just does not seem to be any pattern to it, other than that I am accessing SMART data from one of the drives.

---

