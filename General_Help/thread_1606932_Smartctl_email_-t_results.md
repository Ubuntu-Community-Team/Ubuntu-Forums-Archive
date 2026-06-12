---
title: "Smartctl email -t results"
date: 2010-10-27
forum: General Help
---

### Post by thelamer on 2010-10-27
I am currently trying to setup a box to automate testing and wiping hard drives. 

I use the same commands and am tired of monitoring it.

What I would like is the results of (well actually many drives but lets start out simple; 

smartctl --test=long /dev/sda

To be emailed or broadcast upon completion.

BTW I know smartd can be configured to email when errors are found, but only if errors are found I want a clean bill of health email and some kind of output so it can autostart the wiping process. 

Please let me know if this is possible. 

Thanks!

---

### Post by dcstar on 2010-10-27
> **thelamer said:**
> I am currently trying to setup a box to automate testing and wiping hard drives. 

I use the same commands and am tired of monitoring it.

What I would like is the results of (well actually many drives but lets start out simple; 

smartctl --test=long /dev/sda

To be emailed or broadcast upon completion.

BTW I know smartd can be configured to email when errors are found, but only if errors are found I want a clean bill of health email and some kind of output so it can autostart the wiping process. 

Please let me know if this is possible. 

Thanks!

```
smartctl --test=long /dev/sda | mail whatever-else-mail-needs
```

---

### Post by thelamer on 2010-10-27
That won't work as the commands output is a time to completion. IE: 

```
smartctl --test=short /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Wed Oct 27 01:11:12 2010
```


Selftest command outputs the status but it is just supposed to be run after you know it is done; 

```
smartctl -l selftest /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3508      
```   -

---

### Post by streat on 2013-03-30
Ever figure this out "thelamer"?

---

### Post by howefield on 2013-03-30
Old thread closed.

Feel free to start afresh.

---

