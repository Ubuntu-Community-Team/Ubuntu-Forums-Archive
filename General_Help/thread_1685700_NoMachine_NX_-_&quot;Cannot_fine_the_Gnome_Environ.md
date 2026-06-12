---
title: "NoMachine NX - &quot;Cannot fine the Gnome Environment&quot;"
date: 2011-02-11
forum: General Help
---

### Post by g33kdot on 2011-02-11
*** "Cannot find the Gnome Environment" error when trying to connect to a NXServer with an NXClient on a local area network. ***

To preface, I have used NoMachine before. A few years ago, on dapper or edgy, I used the nomachine nx server implementation and used it extensively. Didn't quite have a need for it for a while, and now, on Lucid and Maverick, I am having -way- -too- -many- -troubles- ... ](*,)

And after 3 hours of fiddling, searching forums, google, config files, and encouraging premature baldness, I am at a loss... *sigh*

The setup: Desktop with full Lucid 10.04, gnome, compiz, mobloquer, ufw. Laptop with BARE Maverick 10.10, gnome, no compiz, no mobloquer, ufw, metacity compositing. I say bare because I used the minimal install cd and only installed the basic components i needed for gnome and ubuntu, to cut down on ram (ie, i did not use ubuntu-desktop metapackage). Here's the kicker, NX works perfectly on Laptop and not so much on Desktop. HA.

The problem: displaying the gnome desktop when connecting to the Desktop machine. I get an error after authentication and session stuff completes. It's about to display the desktop, has the full black screen about to load it, and then a msg box appears... "Cannot find the Gnome environment. Please contact the system administrator.". After trying to hold back from screaming "i AM the system administrator, b%&#@!" *breathe*, i try a multitude of solutions.

What works:
- Desktop to Laptop, NX connection
- Laptop to Desktop, ssh terminal connections
- Laptop to Desktop, VNC using vinagre and vino.

What I've tried:
- connecting from Laptop to Desktop, results in above error.
- connecting from Desktop to Laptop, works great.
- disabling both mobloquer and ufw on both machines, where appropriate. 
- adding correct rule to allow connection on both ufw.
- complete reinstall of nx on Desktop, removing the /usr/NX and ~/.nx directories after removal and before reinstalling.
- checked logs on both machines, after attempting connection to server (see below)
- checked node.cfg and server.cfg in /usr/NX/etc
- checked folder permissions and ownership of authorized_keys2 folder in ~/.ssh
- disabling all settings in the NXClient under Display > Use Custom Settings (composite extension, etc)
- disabling compiz on Desktop
- restarting Desktop
- made sure "gnome-desktop-environment" and "xorg" packages were installed on Desktop
- made sure the node.cfg entry to start "/etc/gdm/Xsession gnome-session" worked... chaos ensued after the attempt, but it did work.
- checked /etc/ssh/sshd_config for PasswordAuthentication yes, and UsePam yes, on both machines
- reinstalled OpenSSH server, purging from synaptic, and removing ~/.ssh folder.

*** I'm fairly convinced that this is a problem with the server/node on the Desktop, as all the msgs in the logs only appear on the server end where I'm connecting. And I can connected to the Laptop just fine.

Log Output:

Desktop --
-----------------------------------------------------------------
```
NXSERVER-3.4.0-15[869]: User 'g33kdot' logged in from '192.168.1.13'. 'NXLogin::set'
NXSERVER-3.4.0-15[869]: Selected node host:localhost with port:22 'main::selectNode'
NXSERVER-3.4.0-15[869]: Current selected node: localhost is in status: running  'main::selectNode'
NXSERVER-3.4.0-15[869]: Selected session type: unix-gnome allowed in the profile of user: g33kdot 'NXShell::Static'
NXSERVER-3.4.0-15[869]: Session '712199C028BB6E2DA6E6B5EB62536019' started by user 'g33kdot'. 'NXShell::handler_session_start'
NXSERVER-3.4.0-15[869]: User 'g33kdot' from '192.168.1.13' logged out. 'NXLogin::reset'
NXNODE-3.4.0-16[1240]: Using port '1002' on node 'g33k-desktop' for session 'unix-gnome'. Logger::log nxnode 6246
NXNODE-3.4.0-16[1240]: Using host from available host list: '192.168.1.10'. Logger::log nxnode 6247
NXNODE-3.4.0-16[1240]: Session 'unix-gnome' on port '1002' closed. Logger::log nxnode 6533
NXSERVER-3.4.0-15[1273]: session sessionId:712199C028BB6E2DA6E6B5EB62536019 finished 'NXShell::handler_session_start'
NXSERVER-3.4.0-15[1273]: Session '712199C028BB6E2DA6E6B5EB62536019' closed by user 'g33kdot'. 'NXShell::Static'

```

Laptop -- (worked, despite the 2 minor errors)
------------------------------------------------------------------
```
NXSERVER-3.4.0-15[26566]: User 'g33kdot' logged in from '192.168.1.10'. 'NXLogin::set'
NXSERVER-3.4.0-15[26566]: Selected node host:localhost with port:22 'main::selectNode'
NXSERVER-3.4.0-15[26566]: Current selected node: localhost is in status: running  'main::selectNode'
NXSERVER-3.4.0-15[26566]: Selected session type: unix-gnome allowed in the profile of user: g33kdot 'NXShell::Static'
NXSERVER-3.4.0-15[26566]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
NXSERVER-3.4.0-15[26566]: Session 'E3EC4088068CAC32946A043EE2AA0277' started by user 'g33kdot'. 'NXShell::handler_session_start'
NXSERVER-3.4.0-15[26566]: ERROR: run command: no child process with pid 26602 Logger::log nxserver 3130
NXSERVER-3.4.0-15[26566]: User 'g33kdot' from '192.168.1.10' logged out. 'NXLogin::reset'
NXNODE-3.4.0-16[26626]: Using port '1001' on node 'g33k-laptop' for session 'unix-gnome'. Logger::log nxnode 6246
NXNODE-3.4.0-16[26626]: Using host from available host list: '192.168.1.13'. Logger::log nxnode 6247
```

To sum: I don't know what else to try. I've used NoMachine NX before, and didn't have to fuss with permissions or any of that junk. Could even connect from Windows clients (nothing special, i guess). And it seems that the defaults that Ubuntu set for ssh and the like work fine (had to reinstall openssh and nx, purging configs, just to get as far as I have). 

Oh, and why not just use VNC through SSH tunnel (essentially, what NX is doing anyways), because when I use VNC the response time sucks. When I used NX before, the way it setup the remote session was flawless, where I could make it fullscreen and it would confuse other people because of how smooth it ran. So whatever they do better, I need it. 

And as far as FreeNX, I am used to NoMachine's version, and most people (ubuntu docs) say to use NoMachine's when FreeNX fails. I still might try FreeNX, but for now I need sleep.

Any and all help appreciated. Thanks.

---

