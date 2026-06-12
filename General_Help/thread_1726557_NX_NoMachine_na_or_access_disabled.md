---
title: "NX NoMachine n/a or access disabled"
date: 2011-04-11
forum: General Help
---

### Post by sopel1000 on 2011-04-11
Please help. Everything is ok, but I cannot connect. It shows that service is not available or the NX access is disabled on host. I have installed nx nomachine sucessfully on 2 other servers with 10.04, but on Maverick... everything is ok, but it does not work. SSH is running on non-standard port, but I changed it in NX server.cfg and node.cfg.

Output from auth.log:

> 
Apr 11 15:54:52 SERVER sshd[2254]: Accepted publickey for USER2 from 127.0.0.1 port 43604 ssh2
Apr 11 15:54:52 SERVER sshd[2254]: pam_unix(sshd:session): session opened for user USER2 by (uid=0)
Apr 11 15:54:53 SERVER sshd[2254]: pam_unix(sshd:session): session closed for user USER2



> 
USER@ubuntu1010:/usr/NX/etc$ sudo /usr/NX/bin/nxserver --restart
NX> 123 Service stopped.
NX> 153 Stopping NX server monitor.
NX> 153 NX server monitor already stopped.
NX> 122 Service started.
NX> 999 Bye.
USER@ubuntu1010:/usr/NX/etc$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.
USER@ubuntu1010:/usr/NX/etc$ sudo /usr/NX/bin/nxserver --useradd USER
NX> 801 User: USER uses SSHD authentication.
NX> 900 Adding public key for user: USER to the authorized keys file.
NX> 716 Public key added to: /home/USER/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: USER.
NX> 900 Public key authentication succeeded.
NX> 301 User: USER enabled in the NX user DB.
NX> 999 Bye.
USER@ubuntu1010:/usr/NX/etc$ sudo /usr/NX/bin/nxserver --useradd USER2
NX> 801 User: USER2 uses SSHD authentication.
NX> 900 Adding public key for user: USER2 to the authorized keys file.
NX> 716 Public key added to: /home/USER2/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: USER2.
NX> 900 Public key authentication succeeded.
NX> 301 User: USER2 enabled in the NX user DB.
NX> 999 Bye.
USER@ubuntu1010:/usr/NX/etc$


Output from Windows client.

> 
NX> 203 NXSSH running with pid: 6812
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XX.XX.XX.XX on port: 21XX
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


---

