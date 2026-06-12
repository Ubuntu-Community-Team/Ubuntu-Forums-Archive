---
title: "Nautilus/Dolphin/smbclient can't access samba shares"
date: 2012-07-06
forum: General Help
---

### Post by Rambo Tribble on 2012-07-06
After upgrading to Kubuntu 12.04, the machines so equipped could not access Samba shares. Smbclient could load shares on the local machine, but no remotes and Dolphin/Nautilus timed out without providing any access. 

I found the solution here: [http://ubuntuswitch.wordpress.com/2010/02/05/nautilus-slow-network-or-network-does-not-work/](http://ubuntuswitch.wordpress.com/2010/02/05/nautilus-slow-network-or-network-does-not-work/) 

I am posting this as a pre-emptive offering to others who may encounter the same problem. I could find nothing in these forums addressing this exact problem or solution. 

To reiterate here the above author's solution, the line in smb.conf:
 
; name resolve order = lmhosts host wins bcast 

needs to be uncommented, (remove the semi-colon), and the "host" name moved to the end of the line, as per: 

name resolve order = lmhosts wins bcast host

A reboot completes the process.

---

