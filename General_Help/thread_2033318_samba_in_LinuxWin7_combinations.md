---
title: "samba in Linux/Win7 combinations"
date: 2012-07-26
forum: General Help
---

### Post by palloy on 2012-07-26
I have 3 PCs on my LAN , connected by ethernet .
All have Win 7 Ult, and two also dual boot Lubuntu 12.04 .
All are in workgroup "WORKGROUP".
All have one username and password.
With Win7 running on all PCs, I can access all network shares from all PCs.
I am trying to get to the point where the same is true if one or both are running Lubuntu.

I installed Samba on both Lubuntus - v3.6.3
I have used Samba Server Configuration to create the shares, visible and writeable, and accessible by everybody (only I actually have access).
I have NOT directly modified smb.conf .
I can ping everything from everywhere.

With Lubuntu running on both A and B, and Win7 on C,
A's Dolphin file manager can see the place "Network",
which displays Network, Samba Shares, and Add Network Folder.
Samba Shares displays Workgroup,
Workgroup displays the 3 PCs, A, B and C
B displays it shares OK
C displays nothing, which is wrong
A displays nothing, which is wrong but not really a problem.

B's Dolphin file manager can see the place "Network",
which displays Network, Samba Shares, and Add Network Folder.
Samba Shares displays nothing, which is wrong.

There are other combinations of OSs which I won't go into just now.

I have done testparm on A and B and it doesn't complain.
smbstatus on A and B seems to suggest the server is not running, despite A being able to see B's shares.
==========================
dave@A:~$ smbstatus

Samba version 3.6.3
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

dave@A:~$
========================
dave@B:~$ smbstatus

Samba version 3.6.3
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

dave@B:~$
====================

I have  tried  "starting samba" but it doesn't work.
I have tried more of the tests at file:///usr/share/doc/samba/diagnosis.html
but since I don't know the jargon or what I'm doing, I haven't changed anything.
Can someone please help.

---

### Post by HiImTye on 2012-07-27
the machines whose shares aren't accessable, can they see their own shares on the network?

---

### Post by palloy on 2012-07-27
"A" can see that it is a member of Workgroup, but expanding Samba Shares/workgroup/A/ brings up a username-password dialogue (that doesn't seem necessary because the share should be "accessible by everyone") and fails to accept any credentials.

"B" and "C" (Win7) can see their own shares.

Am I right in thinking that each machine should be acting as both an SMB server and client ?

---

