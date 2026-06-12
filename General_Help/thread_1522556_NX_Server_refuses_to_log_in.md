---
title: "NX Server refuses to log in"
date: 2010-07-02
forum: General Help
---

### Post by Bill Day on 2010-07-02
I am running nomachine's nxserver on Lucid Lynx and suddenly the client refuses to log in with the following error:

> NXPROXY - Version 3.4.0

Copyright (C) 2001, 2010 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '18866'.
Session: Starting session at 'Fri Jul  2 09:44:19 2010'.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Fri Jul  2 09:44:38 2010'.
Session: Session terminated at 'Fri Jul  2 09:44:38 2010'.Any suggestions would be appreciated. Thanks.


syslog reads as follows:

```
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: initialization: starting parse of config file '/usr/NX/etc/node.cfg' Logger::log nxserver 1140
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/guests.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals are now blocked ... Logger::log nxserver 2465
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18202]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals are now blocked ... Logger::log nxserver 2465
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18203]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: executing command: '/usr/NX/bin/nxssh -nxauthonly -o 'StrictHostKeyChecking no' -l billday 127.0.0.1 -p 22 -2' 'NXNssUserManager::auth'
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh pid is: 18204 'NXNssUserManager::auth'
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: printing password to nxssh stdin: ******** '(eval)'
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/users.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: getLastParameters: command parameters '--user="billday" --status="suspended,running" --geometry="1280x1024x24+render" --type="unix-gnome"'. NXShell::getLastParameters handlers/nxserver 4841
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:37 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: getLastParameters: command parameters '--link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="williamsonday.org" --type="unix-gnome" --geometry="1280x925" --client="linux" --keyboard="pc105/us" --screeninfo="1280x925x24+render"'. NXShell::getLastParameters handlers/nxserver 2135
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l billday localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec). Stored status. 'Logger::statusPush'
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals are now blocked ... Logger::log nxserver 2465
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh child pid is: 18295 (NXNodeExec). Stored status. 'Logger::statusPush'
Jul  2 09:31:40 bonewagon NXSERVER-3.4.0-12[18295]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:41 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec). Stored status. 'Logger::statusPush'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh process exited with '0' 'NXNodeExec::exec'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals are now blocked ... Logger::log nxserver 2465
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18390]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3209
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3220
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1005 'NXNodeExec::onMessage'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1008 'NXNodeExec::onMessage'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1009 'NXNodeExec::onMessage'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1010 'NXNodeExec::onMessage'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l billday localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec). Stored status. 'Logger::statusPush'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals are now blocked ... Logger::log nxserver 2465
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh child pid is: 18393 (NXNodeExec). Stored status. 'Logger::statusPush'
Jul  2 09:31:42 bonewagon NXSERVER-3.4.0-12[18393]: DEBUG: Signals unblocked Logger::log nxserver 2487
Jul  2 09:31:45 bonewagon NXSERVER-3.4.0-12[18506]: DEBUG: Calling handler function: 'NXUtmp::add' for 'connected to nxnode' event 'NXNodeExec::__onMessageRun'
Jul  2 09:31:45 bonewagon NXSERVER-3.4.0-12[18199]: ERROR: run command: no child process with pid 18295 Logger::log nxserver 3127
Jul  2 09:31:45 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Running nxssh for forwarding session 'NXShell::handler_bye'
Jul  2 09:31:45 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh is now running with pid: 18508 'NXShell::handler_bye'
Jul  2 09:31:45 bonewagon NXSERVER-3.4.0-12[18508]: DEBUG: nxssh command: /usr/NX/bin/nxssh -B -E '(eval)'
Jul  2 09:31:46 bonewagon NXNODE-3.4.0-13[18480]: Using port '1010' on node 'bonewagon.williamsonday.test' for session 'unix-gnome'. Logger::log nxnode 6244
Jul  2 09:31:46 bonewagon NXNODE-3.4.0-13[18480]: Using host from available host list: '192.168.1.25'. Logger::log nxnode 6245
Jul  2 09:31:46 bonewagon NXSERVER-3.4.0-12[18506]: DEBUG: Recived request for a run nxmonitor: '(eval)'
Jul  2 09:31:46 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh switch command to start nxcomp channel: NX> 299 Switch connection to: localhost:5010 in: 3 out: 4\n 'NXShell::handler_bye'
Jul  2 09:31:46 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Read 219 byte/s from nxssh stderr: [NX> 285 Enabling check on switch command#015\nNX> 285 Enabling skip of SSH config files#015\nNX> 285 Setting the preferred NX options#015\nNX> 285 Identified host: localhost port: 5010#015\nNX> 285 Identified descriptors in: 3 out: 4#015\n] 'NXShell::handler_bye'
Jul  2 09:31:46 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Read 41 byte/s from nxssh stderr: [#015\nNX> 291 Connecting to: localhost:5010#015\n] 'NXShell::handler_bye'
Jul  2 09:31:50 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Read 56 byte/s from nxssh stderr: [NX> 294 Connection to: localhost:5010 failed. Retrying#015\n] 'NXShell::handler_bye'
Jul  2 09:31:56 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Read 56 byte/s from nxssh stderr: [NX> 294 Connection to: localhost:5010 failed. Retrying#015\n] 'NXShell::handler_bye'
Jul  2 09:32:01 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Read 56 byte/s from nxssh stderr: [NX> 294 Connection to: localhost:5010 failed. Retrying#015\n] 'NXShell::handler_bye'
Jul  2 09:32:05 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Read 46 byte/s from nxssh stderr: [NX> 290 Failed connection to: localhost:5010#015\n] 'NXShell::handler_bye'
Jul  2 09:32:05 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Closed nxssh stdout: nxssh is exiting ... 'NXShell::handler_bye'
Jul  2 09:32:05 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: Closed nxssh stderr: nxssh is exiting ... 'NXShell::handler_bye'
Jul  2 09:32:05 bonewagon NXSERVER-3.4.0-12[18199]: ERROR: nxssh process exit with exit status: 255 and flag connected set to: [0] 'NXShell::handler_bye'
Jul  2 09:32:05 bonewagon NXSERVER-3.4.0-12[18199]: ERROR: Cannot establish ssh tunnel between nxserver and nxnode 'NXShell::handler_bye'
Jul  2 09:32:05 bonewagon NXSERVER-3.4.0-12[18199]: DEBUG: nxssh finished 'NXShell::handler_bye'

```

---

### Post by pricetech on 2010-07-02
Did it work to begin with, then stop working ??

I noticed your Node and Server show two different versions in the log file.  I've never taken a look to see if mine are different, but you might try a reinstall.

Also, is SSH running on the server ??  It looks like it may be down, though I'm not the best at interpreting logs.

---

### Post by Bill Day on 2010-07-02
Thanks, pricetech, for your suggestions. To be fair, I now realize that I probably didn't include enough information in my original post.  The critical difference that stopped nxserver (and also x2go and vino) from responding was that I had switched from a UFW firewall to using iptables in order to configure a PPTP VPN.  I finally found myself on the right scent (after a lengthy colloquy with Mr. Google) when I started looking at why I couldn't contact the X server.  (SSH was working fine otherwise, and I was even able to tunnel other protocols over SSH.)  I found the solution on this page: [http://www.linuxforums.org/forum/linux-networking/43488-configuring-iptables-ssh-x11-forwarding.html](http://www.linuxforums.org/forum/linux-networking/43488-configuring-iptables-ssh-x11-forwarding.html) .

What I needed to do was make sure that iptables allowed communication on the loopback interface, which I did by adding the following command.

```
#sudo iptables -A INPUT -i lo -j ACCEPT
```A helpful resource in finding just the right language for enabling communication on the loopback interface was LinWiz: [http://www.lowth.com/LinWiz/1.09/ServerFirewall/fw.pl/iptables](http://www.lowth.com/LinWiz/1.09/ServerFirewall/fw.pl/iptables)

---

### Post by pricetech on 2010-07-02
Glad you got it fixed.  Please mark your thread as solved so it might help someone else.

See Thread Tools above on the right.

---

