---
title: "cron cannot find script"
date: 2011-03-25
forum: General Help
---

### Post by insanity54 on 2011-03-25
Hey guys,

I am running a headless Ubuntu 10.04 server. I want to have cron run a script that starts a (virtualbox) virtual machine on startup.

The script runs fine when I'm logged in and I execute it, but when cron tries to run it on boot, I get a system email that says:
```
Return-Path: <insanity54@insane-server>
X-Original-To: insanity54
Delivered-To: insanity54@insane-server
Received: by insane-server (Postfix, from userid 1000)
        id xxxxxxxxxxx; Wed, 23 Mar 2011 20:32:47 -0700 (PDT)
From: insanity54@insane-server (Cron Daemon)
To: insanity54@insane-server
Subject: Cron <insanity54@insane-server> /home/insanity54/scripts/autostart-vbox
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/insanity54>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=insanity54>
Message-Id: <20110324033249.xxxxxxxxxxx@insane-server>
Date: Wed, 23 Mar 2011 20:32:47 -0700 (PDT)

/bin/sh: /home/insanity54/scripts/autostart-vbox: not found
```

I found some similar issues using my Google-Fu that suggested cron does not run in the same environment as the environment I type commands in when I am logged in? This is where I am stuck. I think that somehow my script needs to run in the same environment as cron, or vice-versa, but I have no idea how to accomplish this!

Here is my script:

```
#!/bin/bash#

## Description
#
#       Script made by insanity54
#

## Variables
TimerStart=30
VBoxRun=/usr/bin/vboxheadless\ -s\ "LoonyMachine001" # the actual command that starts the virtual machine.


## Script GO!
echo Waiting $TimerStart seconds to let the system settle.
TimerCurrent=$TimerStart                                        # a count down.
while [ $TimerCurrent -ge 1 ]; do                               # counting down.
  echo Time Remaining $TimerCurrent                             # same as last... 
  let TimerCurrent-=1                                           # almost done.
done                                                            # count down finished.

echo Timer done, starting LoonyMachine001 virtual machine.
$VBoxRun

echo Script is done. Exiting.
```

Here is my crontab:

```

# m h  dom mon dow   command

@reboot /home/insanity54/scripts/autostart-vbox
```

Can anyone help me help cron find my script?

P.S. I read that an init.d scripts are be better than using cron for running services I originally tried getting a init.d script working for this purpose using several guides on here (the forum) and on the internet, but I couldn't get other's scripts to work. At the moment, I don't need to be able to start/stop and see status on command or have the virtual machine stop when the system is going down. All I need is a bareboned, super simple script to start a virtual machine.

---

### Post by DaithiF on 2011-03-25
don't suppose you have an encrypted home directory?

---

### Post by insanity54 on 2011-03-29
Hi DaithiF, thanks for your reply.

> **DaithiF said:**
> don't suppose you have an encrypted home directory?

I don't know... If it's default on ubuntu server 10.04 then I guess that's a yes?

If there's a file called .encryptfs in my home directory does that mean that it's encrypted?

I ran: ```
ls -la
``` in /home/insanity54/

output:```

lrwxrwxrwx 1 insanity54  insanity54     29 2011-02-11 16:46 .ecryptfs -> /home/.ecryptfs/insanity54/.ecryptfs

```

If it is encrypted, would putting the script somewhere other than /home/ be worth trying?

---

### Post by DaithiF on 2011-03-30
Its not a default, but the presence of that file probably does mean that yours in encrypted.  Maybe you selected that option during install without noticing.

For a server an encrypted home directory may not make a lot of sense ... its more of use for portable devices (ie. ones that could be lost / stolen).  And it complicates server administration because the directory is only accessible when that user is logged in ... which you're discovering with your failed cron job.

If I were you and if encryption isn't a particular requirement then I would start again (ie. do a reinstall) ... server admin can be complicated enough without throwing encrypted dirs into the mix too.  Maybe theres an easy way to turn off the encrypted directory (ie. without doing a reinstall).  Take a look here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) as a starting point.

---

### Post by insanity54 on 2011-04-05
Yes, my home directory was encrypted, and yes, that was what was causing the problem. I made a new user account and moved the script to that user's home directory, then edited crontab to reflect the new location. 

This problem is technically solved, but my script still doesn't work! I get this:

```
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.32-30-server) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
VBoxHeadless: Error -1908 in suplibOsInit!
VBoxHeadless: Kernel driver not installed

VBoxHeadless: Tip! Make sure the kernel module is loaded. It may also help to re
install VirtualBox.
Script is done. Exiting.
```

I think this is a question for the visualization section though.

Anyway, DaithiF, thank you for your help!

---

