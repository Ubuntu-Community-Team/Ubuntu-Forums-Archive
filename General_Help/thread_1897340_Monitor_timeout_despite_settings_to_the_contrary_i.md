---
title: "Monitor timeout despite settings to the contrary in power management"
date: 2011-12-19
forum: General Help
---

### Post by xluke on 2011-12-19
Hello,
I went to ->System Settings -> Power and changed everything to "do nothing" but nevertheless the screen shuts off after about 10 minutes and the session also locks.  How do I avoid this?

I'm on a thinkpad w520.

Linux is endless frustration.  

Thanks!

---

### Post by Maleificus on 2011-12-19
One solution (it's more of a workaround actually) is to add the following code to your xorg.conf 

Section "ServerFlags" 
 Option "BlankTime"   "0"    
 Option "StandbyTime" "0"    
 Option "SuspendTime" "0"    
 Option "OffTime"     "0"    
 Option "DontZap" "false" 
EndSection

This will also disable your screen saver.

---

