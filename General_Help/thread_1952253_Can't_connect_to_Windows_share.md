---
title: "Can't connect to Windows share"
date: 2012-04-03
forum: General Help
---

### Post by daehenoc on 2012-04-03
Hi all,

I've recently started at a new job and are having problems connecting to the Active Directory shares with Ubuntu.

I'm currently on a Windows laptop and can see the server and share names as the currently mapped drive, e.g. U: domain.server.com.bla/share
I have installed VirtualBox and have got an Ubuntu VM running with networking.

I can see that share by using smbclient, however there are some errors when I do this list:
```
$ smbclient -L //domain.server.com.bla/groups -U myusername -W domain.server.com.bla
Enter myusername's password: 
Domain=[STAFF] OS=[Windows Server (R) 2008 Enterprise 6002 Service Pack 2] Server=[Windows Server (R) 2008 Enterprise 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	C$              Disk      Default share
	D$              Disk      Default share
	groups          Disk      
	users           Disk      
session request to DOMAIN.SERVER.CO failed (Called name not present)
session request to STAFF failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```And when I attempt to connect to the groups share:
```
$ smbclient //domain.server.com.bla/groups -U myusername -W domain.server.com.bla
Enter myusername's password: 
Domain=[STAFF] OS=[Windows Server (R) 2008 Enterprise 6002 Service Pack 2] Server=[Windows Server (R) 2008 Enterprise 6.0]
Connection to SERV01 failed (Error NT_STATUS_BAD_NETWORK_NAME)
```So I'm seeing this last line here with 'SERV01' in it, and I can ping SERV01.DOMAIN.SERVER.COM.BLA successfully.

I've googled NT_STATUS_BAD_NETWORK_NAME and didn't find anything useful, or which could resolve my problem.

Any ideas about how to fix this?  I can definitely access the share in Windows!

I get the feeling that they have turned some services off on the Windows share servers which smb-type connections require...

---

