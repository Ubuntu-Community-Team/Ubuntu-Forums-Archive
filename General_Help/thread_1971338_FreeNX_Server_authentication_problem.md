---
title: "FreeNX Server authentication problem"
date: 2012-05-02
forum: General Help
---

### Post by reader4 on 2012-05-02
I recently moved a workstation to 11.10.  I had to reinstall the NX server from NoMachine using the links here:

[http://www.nomachine.com/download-package.php?Prod_Id=3594](http://www.nomachine.com/download-package.php?Prod_Id=3594)

I also upgraded my client.  I deleted all of the .ssh/known_hosts files, configuration files and logs.  However, I am still getting a user authentication error when trying to login.  I prefer to keep the default key so that anyone in my research group can access the workstation without having to install the key, etc. (we are on a very secure, internal-only network anyway).  The client syslog shows:

NX> 203 NXSSH running with pid: 21652
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: myhost on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.5.0-9 - LFE
NX> 105 Hello NXCLIENT - Version 3.5.0
NX> 134 Accepted protocol: 3.5.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: myuser
NX> 102 Password: *********
NX> 404 ERROR: wrong password or login.
NX> 999 Bye.
NX> 280 Exiting on signal: 15

So user authentication is not working. NoMachine FAQs appear outdates, since the commands suggested are no longer supported:

[http://www.nomachine.com/ar/view.php?ar_id=AR02C00165](http://www.nomachine.com/ar/view.php?ar_id=AR02C00165)

I have tried everything I have seen on the internet or can think of, but the root problem appears to be related to SSH authentication for the user.  However, I can SSH to the machine without problem.  Has anyone seen this, or does anyone have suggestions to try?  I've spent a day on this already...

---

### Post by wfurn on 2012-05-02
Anything interesting in /var/log/auth.log?

---

### Post by reader4 on 2012-05-02
Not really:

May  2 15:08:48 myhost sshd[2600]: Accepted publickey for nx from myclient port 61762 ssh2
May  2 15:08:48 myhost sshd[2600]: pam_unix(sshd:session): session opened for user nx by (uid=0)
May  2 15:08:49 myhost sshd[2600]: pam_unix(sshd:session): session closed for user nx

The log looks fine for my SSH login:

May  2 14:33:41 myhost sshd[2160]: Accepted password for myuser from myclient port 61214 ssh2
May  2 14:33:41 myhost sshd[2160]: pam_unix(sshd:session): session opened for user myuser by (uid=0)


Other thoughts?

---

### Post by reader4 on 2012-05-17
Getting back to this problem... still no solutions.  The server is updated to 12.04 now.  Laster working version of Ubuntu was 10.10.  I can still connect to the server via terminal+SSH, but there is an authentication problem when I try to login using the NX client.  Does anyone have NX working on 11.10+?  Anyone have any tips on troubleshooting the problem.  Am stuck in the mud right now and this machine is typically used remotely, so this is a big issue for us.

Thanks.

---

