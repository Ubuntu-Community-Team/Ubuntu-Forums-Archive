---
title: "ssh login graphically"
date: 2009-07-30
forum: General Help
---

### Post by metalcoat on 2009-07-30
Here is the background, I recently updated from a remote location via ssh and had to reboot.  I want to be able to vnc in however the script to start up is not launched until the kde session is started after login.  Is there a way to force login graphical wise?

---

### Post by Zorael on 2009-07-30
Far from knowledgeable in this area, but as a workaround you should be able to set up autologin from that ssh session (by modifying /etc/kde4/kdm/kdmrc), and then restart kdm.
```
# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
[B]# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=true[/B]
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
[B]# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true[/B]
# See above
ClientLogFile=.xsession-errors
```
With AutoLoginLocked you'd at least retain a modicum of security since they'd have to enter your password to actually be able to do anything.

---

### Post by metalcoat on 2009-08-02
Never thought about an automatic login script.  Worked a charm!  Thanks:D

---

