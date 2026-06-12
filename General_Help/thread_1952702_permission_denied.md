---
title: "permission denied?"
date: 2012-04-04
forum: General Help
---

### Post by jacob70 on 2012-04-04
I decide to run Ubuntu side by side with Windows 7, but during the installation this odd error message kept popping up. I cant remember what it said, but it was directly affecting it so i didnt think much of it. When it was finished a pop up came up saying "Error Permission Denied". Mine is the only user on this PC, and I dont know what wrong. Any help?

The error i noticed before says "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk\DR2. Im not an extremelly techy person so i dont know what to do. Help?

---

### Post by Frogs Hair on 2012-04-04
Did you attenpt install via Wubi ? [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
If so , try running starting Wubi as administrator with a right click .

---

### Post by bcbc on 2012-04-05
The 'no disk' error is bug [lpbug]365881[/lpbug]. Just click through it.

The permission denied at the end could be bug [lpbug]862003[/lpbug]. It's best to review the log file (in the %TEMP% folder) and compare to the bug report, or just post the log file here.

---

### Post by jacob70 on 2012-04-05
Im sure its just a small bug. I tried running as admin and it said it was already installed. I restarted and sure enough Ubuntu was there, and let me  just say it's beautiful. As a first time user im having a few difficulties but my god Im loving this OS.

---

### Post by bcbc on 2012-04-05
Yeah, if rebooting worked then it's bug 862003.

When using Wubi, make sure you don't perform hard shutdowns/reboots: [https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

Enjoy!

---

