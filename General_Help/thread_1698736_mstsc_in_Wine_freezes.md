---
title: "mstsc in Wine freezes"
date: 2011-03-02
forum: General Help
---

### Post by rva1945 on 2011-03-02
If I navigate to the c:\windows\system32 and right-click on mstsc.exe, open with Wine, after logging with user and password in the Windows TS (at the office) when I click on Connect, it freezes, the window goes blank and I have to force it to quit.

The reason I want to run it is that the Windows Server 2003 R2 doesn't accept any Linux client.

I used to access from the XP partition, which doesn't boot anymore so I try to run its mstsc.exe app from Wine.

Is there something I could do? Is it about Wine configuration?

---

### Post by CrazyGuy123 on 2011-05-02
This seems to be a new bug in wine.

Old versions of ubuntu work fine.  I have yet to track down the exact problem.  It seems to affect all versions of mstsc.exe.

The symptoms are mstsc(Windows Remote Desktop Client) runs fine while in the initial dialogue box where the user selects the host to connect to, but freezes upon clicking connect.

The freeze occurs very early in the connection process, since it occurs even if the connection address is invalid.  There don't seem to be any telltale signs in the wine console output.

I have tried turning off all the peripheral options, such as sound, drive, printer, etc. redirection incase initialising those devices was causing the freeze.

---

