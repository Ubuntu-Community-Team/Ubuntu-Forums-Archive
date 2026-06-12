---
title: "Linux (ubuntu) Terminal for Windows 7?"
date: 2012-07-23
forum: General Help
---

### Post by derekpock on 2012-07-23
I have found the Linux Terminal to be very effective and much more useful than the Windows CMD. Is there any way to download it and use it for general tools in Windows 7?

---

### Post by cbraxton on 2012-07-23
Probably the closest you're going to get to that is Cygwin, which provides a Unix/Linux-like environment and shell on Windows. See [http://www.cygwin.com](http://www.cygwin.com) for details.

---

### Post by codemaniac on 2012-07-24
> **derekpock said:**
> I have found the Linux Terminal to be very effective and much more useful than the Windows CMD. Is there any way to download it and use it for general tools in Windows 7?


Some time I need to work with on Windows Servers and i use powershell to automate things .
PowerShell provides full access to COM and WMI , enabling administrators to perform administrative tasks on both local and remote Windows systems .

It is much more powerful and versatile than cmd.exe .However million miles to go to catch up Unix shell utilities in text processing . ;)

EDIT : awk/grep/sed don't work against COM, WMI, ADSI, the Registry, the cert  store, etc, etc.  In other words, UNIX is an entire ecosystem self-tuned  around text files.Windows is a completely different ecosystem self-tuned around APIs and Objects. Hence in order to manipulate these objects in windows environment traditional unix utilities wont be of help .

---

