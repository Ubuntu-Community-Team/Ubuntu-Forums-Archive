---
title: "setting up kixtart logon script with samba PDC"
date: 2010-07-07
forum: General Help
---

### Post by nixnotwin on 2010-07-07
I am trying to setup samba as a primary domain controller. I am using Ubuntu Lucid desktop edition. I couldn't get kixtart logon script working. Here are the settings I did: 

> **nixnotwin said:**
> I was not able to get kixstart working on my  network.

This is the content of my logon.bat file

```
@ECHO OFF 
::  Network logon script 
::  Use KiXtart to manage network logons 
%0\..\Kix32.exe %0\..\kixtart.kix /f                      
```This is  the content of my kixtart.kix file
```

break on 
; delete all mappings 
 
USE * /delete 
 
; And here is one group-oriented script to show what can be 
; done that way: 
IF INGROUP("DOMAIN1\group1") 
USE R: \\SMBSERVER\teefiles 
IF INGROUP("DOMAIN1\group2") 
USE N: \\SMBSERVER\myfiles 

```In smb.conf files I have the entry "logon script = logon.bat"

And also entries for the shared directories with group access  permissions in the smb.conf file

I followed this guide [http://ubuntuforums.org/showthread.php?t=1499753](http://ubuntuforums.org/showthread.php?t=1499753)

---

