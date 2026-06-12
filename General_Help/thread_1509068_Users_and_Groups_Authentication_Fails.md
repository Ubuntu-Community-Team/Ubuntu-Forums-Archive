---
title: "Users and Groups Authentication Fails"
date: 2010-06-13
forum: General Help
---

### Post by cwarner7_11 on 2010-06-13
I recently tried installing a new version of VirtualBox PUEL version, after uninstalling an earlier version.  But the major issue I have now is that I can no longer modify my User Settings.  Clicking on the "Autnenticate" icon gets me a failure notice:  "System policy prevents modifying the system configuration", with details reading "Action: org.freedesktop.systemtoolsbackends.set". Hovering over this link says to click on the link to edit the file, but nothing happens.  Searching the file system tells me this file does not exist.
Prior to this episode with VirtualBox, I had no trouble modifying Users and Groups.  I was able to remove a group from the command line, but the cannot get the GUI authorization to work.  I have searched the forums and bugs for similar problems, and, although there appear to be a number of similar issues, no where can I find any clear information on how this system is supposed to work, or what I need to do to correct the problem.  Any suggestions?

---

### Post by sisco311 on 2010-06-13
Is your user in the admin group?
```
groups
```

Can you use policykit?
```
pkexec echo "OK"
```

What's the output of:
```
pkaction --verbose | grep -A8 org.freedesktop.systemtoolsbackends
```?

---

### Post by cwarner7_11 on 2010-06-13
Is my user in the admin group?  Yes.  I have added users and changed groups in the past with no problem.  The problem arose when I was trying to upgrade VirtualBox.

Can I use policykit?   Here is what I get:

rocketman@rocketman-desktop:~$ pkexec echo "OK"
Not authorized.
rocketman@rocketman-desktop:~$ sudo pkexec echo "OK"
[sudo] password for rocketman: 
User of caller (1000) does not match our uid (0)

And:

rocketman@rocketman-desktop:~$ pkaction --verbose | grep -A8 org.freedesktop.systemtoolsbackends
org.freedesktop.systemtoolsbackends.self.set:
  description:       Change the user's own account configuration
  message:           System policy requires you to authenticate in order to modify your user account information
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_self
--
org.freedesktop.systemtoolsbackends.set:
  description:       Manage system configuration
  message:           System policy prevents modifying the system configuration
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

It is possible that a recent update may have corrupted something- it has been months since I have done any work with Users and Groups, so it may not be related to the attempt to upgrade VirtualBox.

This, by the way, is in Ubuntu 9.10 Server 64-bit.

---

