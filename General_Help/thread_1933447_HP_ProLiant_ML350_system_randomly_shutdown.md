---
title: "HP ProLiant ML350: system randomly shutdown"
date: 2012-02-29
forum: General Help
---

### Post by oceanyounger on 2012-02-29
I have a linux server HP ProLiant ML350. Recently it randomly shuts down with following info in syslog, maybe after I upgraded the system to relatively latest Ubuntu (10.04?)
   
  Feb  7 16:08:06 shenzhen-linux AptDaemon: INFO: Initializing daemon
  Feb  7 16:13:06 shenzhen-linux AptDaemon: INFO: Quiting due to inactivity
  [COLOR=#C00000]Feb  7 16:13:06 shenzhen-linux AptDaemon: INFO: Shutdown was requested[/COLOR]
   
  Do you have any idea of this error? 
  I searched in the forum, someone says it is due to the incompatibility between BIOS and Ubuntu system, so suggest to upgrade BIOS.
  [http://ubuntuforums.org/showthread.php?t=1497384](http://ubuntuforums.org/showthread.php?t=1497384)
  However it is hard to upgrade BIOS under Linux (original system on this server is Windows).


Any other way to work around this issue?

---

### Post by jrutherfordt on 2012-03-01
I've updated a bios from a live cd that had ntfs dos and a copy of the bios flash .exe file on a usb drive.  That's if the bios flash is compatible with dos, being a server it should be but you never know.  Good luck.

---

