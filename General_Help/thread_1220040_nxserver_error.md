---
title: "nxserver error"
date: 2009-07-22
forum: General Help
---

### Post by |VeN| on 2009-07-22
Hi there,

I've been trying to setup a remote desktop environment for a new machine. In the past I have use vncserver and tightvnc to remote in from a windows desktop on a home network.

Now im trying to set access up through SSH so this box can be accessed from anywhere. Using various threads I was able to get nxserver running but when i try to connect from a windows machine(not local) using the nxclient i get the following problem:

```
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXNODE-3.3.0-17[4035]: getting agent pid: cannot read pid file '/home/bcasadmin/.nx/C-W-AMNYC-D-FACL07-1011-B1D92E4BC51800560A6154BA3049E5CE/pids/agent'. Exiting. main::get_agent_pid nxnode 8829
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXNODE-3.3.0-17[4035]: directory '/home/bcasadmin/.nx/C-W-AMNYC-D-FACL07-1011-B1D92E4BC51800560A6154BA3049E5CE' moved into '/home/bcasadmin/.nx/F-C-W-AMNYC-D-FACL07-1011-B1D92E4BC51800560A6154BA3049E5CE' for investigation Logger::log nxnode 8886
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 ERROR: NXNODE Ver. 3.3.0-17  (Error id e517C4B)
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 ERROR: create session: run commands
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 ERROR: execution of last command failed
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 last command: /bin/bash --login -c '/usr/X11R6/bin/xauth -v source /home/bcasadmin/.nx/C-W-AMNYC-D-FACL07-1011-B1D92E4BC51800560A6154BA3049E5CE/scripts/authority'
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 exit value: 1
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 stdout: 
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 stderr: /usr/X11R6/bin/xauth:  error in locking authority file /home/bcasadmin/.Xauthority
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NX> 596 init: stdin arguments: user=bcasadmin,userip=65%2e200%2e165%2e103,uniqueid=B1D92E4BC51800560A6154BA3049E5CE,display=1011,node_number=0,server_name=W%2dAMNYC%2dD%2dFACL07,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e1%2e66,encryption_mode=3,connection=local,images=64M,cache=32M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=BCASNEW,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1024x768x32%2brender,keyboard=pc102%2fen_US,geometry=1024x768,link=wan
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NXNodeExec::exec('startsession', 'user=bcasadmin&userip=65%2e200%2e165%2e103&uniqueid=B1D92E4BC518...', 'localhost', 21277) called at handlers/nxserver.pl line 3533
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NXShell::handler_session_start('--link="wan" --backingstore="1" --encryption="1" --cache="32M" -...') called at NXShell.pm line 373
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NXShell::handle_command('startsession', '--link="wan" --backingstore="1" --encryption="1" --cache="32M" -...') called at NXShell.pm line 145
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) NXShell::run() called at nxserver.pl line 4470
Jul 22 08:41:22 W-AMNYC-D-FACL07 NXSERVER-3.3.0-22[4001]: ERROR: (exception id 6643A6B9) eval {...} called at nxserver.pl line 4429
```

I've tried to change the ownership of the .Xauthority dir and all sub dir's & files but with still get the same error.

Any help is very much appreciated.

---

### Post by |VeN| on 2009-07-24
SOLVED!

Sorry the .Xauthority directory wasn't the issue. It was the .Xauthority file!

chown'ed the file and now im in!

---

