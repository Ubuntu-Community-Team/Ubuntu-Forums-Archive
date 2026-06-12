---
title: "Shorewall/SMB issue"
date: 2006-04-29
forum: General Help
---

### Post by saphil on 2006-04-29
I have set up shorewall on this file server.  Ubuntu 5.10, x86 and the SMB shares to the windows boxes on the network no longer work.  The printer attached to one of the windows boxes is also, not surprisingly, not accessible from this machine.  I found the main shorewall manual online (Internet works) and it says to put the following rule in.  However it doesn't say what file to put the rule into.

#ACTION   SOURCE   DEST   PROTO    DEST PORT(S)   SOURCE
#                                                 PORT(S)
SMB/ACCEPT  $FW      loc
SMB/ACCEPT  loc      $FW I have commented out the lines that deny or reject SMB  /etc/shorewall/action.Drop and /etc/shorewall/action.Reject 

The /etc/shorewall/action.DropSMB and RejectSMB files is still in the folder and I commented out all the lines with #  It still didn't work

I added the above lines to the /etc/shorewall/action.AllowSMB
Shorewall didn't like the target and failed to restart.  

I changed the $FW to the actual name of my firewall zone
Shorewall didn't like the target and failed to restart.

I changed the command SMB/ACCEPT to just ACCEPT
Shorewall restarted, but it still doesn't show any servers with shares in the network servers window.  I restarted the SMB server and still no servers in the network servers window

---

