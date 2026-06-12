---
title: "Installing VB6 Runtimes for old Windows program"
date: 2010-02-28
forum: General Help
---

### Post by jereece on 2010-02-28
I have an old reminder program designed back in the Windows 3.1 era. It works at least up through Windows XP.  I have not tried it on Vista or Windows 7.  I am trying to get it to run on Ubuntu 9.10.  This program installed via Wine with no problems.  When I launch the program, I get the splash screen but the program itself never loads.  I know it requires the VB6 runtimes and I don't think those are included in the program setup. I think this is the problem. 

My question is, can I install the VB6 runtimes (vbrun60sp5.exe) via Wine or do I need to manually place the VB6 runtimes somewhere on the drive?

Any help is deeply appreciated.  I am still learning about Ubuntu.

Thanks,
Jim

---

### Post by spcwingo on 2010-02-28
If you're running the program via WINE then you would also have to install VB6 runtime via WINE for the two to work together.  ;)

---

### Post by jereece on 2010-02-28
I tried to install it via Wine but not sure it worked.  It launches and for a split second appears to copy the file somewhere, but when I browse Wine C: and look in Windows/System or System32 it's not there.  I tried to find the actual dll file on the internet but so far all I can find is the executable.

---

### Post by spcwingo on 2010-02-28
Have you tried running from the terminal to see if there are error messages.  For example if the VB installer is in your home directory, try running it from the terminal with this command:

```
wine "/home/your_username/vbrun60sp5.exe"
```

---

