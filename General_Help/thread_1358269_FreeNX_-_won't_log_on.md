---
title: "FreeNX - won't log on"
date: 2009-12-18
forum: General Help
---

### Post by Eivind Lowzow on 2009-12-18
Hi.
Can anyone help med with this?:
 
On my Ubuntu 9.10 I have installed the FreeNX server. On my XP I have installed Nomachine client. Try this over LAN and have difficulties to log on.
 
When logging on the first time after installing FreeNX, I get this message from NX:
"The authenticity of host 192.168.0.101 can't be established.
The RSA key fingerprisnt is:
[a long row numbers and letters seperated with colon.]
Are you sure you want to continue connecting?"
 
I choose YES.
 
New message:
"The NX service is not available or the NX access was disabled on host 192.168.0.101"
 
Details show:
"NX> 203 NXSSH running with pid: 26955
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.101 on port: 22
NX> 211 The authenticity of host '192.168.0.101 (192.168.0.101)' can't be established.
RSA key fingerprint is ff:f2:ac:e0:a9:cf:bc:ef:2e:52:ee:e9:09:a3:2a:ec.
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added '192.168.0.101' (RSA) to the list of known hosts.
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: eivind
NX> 102 Password: 
NX> 103 Welcome to: Bergen user: eivind
NX> 105 listsession --user="eivind" --status="suspended,running" --geometry="1600x1200x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'eivind' for reconnect:
 
Display Type Session ID Options Depth Screen Status Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
 
 
NX> 148 Server capacity: not reached for user: eivind
NX> 105 startsession --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Lokalt" --type="unix-gnome" --geometry="1600x1200" --client="linux" --keyboard="pc105/no" --screeninfo="1600x1200x24+render" 
 
/usr/bin/nxserver: line 448: /var/lib/nxserver/db/running/sessionId{4EBBDD530F245F8439B78857013BE01B}: Permission denied
cat: /var/lib/nxserver/db/running/sessionId{4EBBDD530F245F8439B78857013BE01B}: No such file or directory"

---

