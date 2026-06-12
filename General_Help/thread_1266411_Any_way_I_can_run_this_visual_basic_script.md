---
title: "Any way I can run this visual basic script?"
date: 2009-09-14
forum: General Help
---

### Post by Harlequin. on 2009-09-14
I need to run a visual basic script that fixes a problem for a game I play (it's ran in WINE).

When I execute the script it just comes up in mousepad lol :[.


I'm running Xubuntu 9.04 if it makes a difference. Thanks in advance.

---

### Post by i.r.id10t on 2009-09-14
Run it with wine, just like your game.  Or read the script, see what it does and make the changes yourself.

---

### Post by Harlequin. on 2009-09-14
> **i.r.id10t said:**
> Run it with wine, just like your game.  Or read the script, see what it does and make the changes yourself.

It's .vbs, I can't run it in WINE... Or at least I don't know how to...

This is the script:

> Dim ErrorFlag
'Create a shell object
Set Shell = WScript.CreateObject("WScript.Shell")
'Create a file system object
Set FSO = WScript.CreateObject("Scripting.FileSystemObject")
'Get path to Diablo II EXE from registry
Reg1 = "HKLM\Software\Blizzard Entertainment\Diablo II"
Reg2 = "HKCU\Software\Blizzard Entertainment\Diablo II"
Reg1Use = True
Reg2Use = True
'Ensure script gets to clean up if setting up and launching the mod fails
On Error Resume Next
Set Folder = FSO.GetFolder(".")
D2Path = Folder.Path & "\"

Shell.RegWrite "HKCU\Software\Blizzard Entertainment\Diablo II\InstallPath", Folder.Path, "REG_SZ"
Shell.RegWrite "HKLM\Software\Blizzard Entertainment\Diablo II\InstallPath", Folder.Path, "REG_SZ"
Shell.RegWrite "HKCU\Software\Wow6432Node\Blizzard Entertainment\Diablo II\InstallPath", Folder.Path, "REG_SZ"
Shell.RegWrite "HKLM\Software\Wow6432Node\Blizzard Entertainment\Diablo II\InstallPath", Folder.Path, "REG_SZ"
WScript.Quit(0)

I've done the registry editing, but it doesn't seem to have changed anything.

---

### Post by Harlequin. on 2009-09-14
Google says 

"VBS in Linux. It works fine running in WINE.
You just have to install the Windows Script Host.
And you may need to hand-register the COM
DLLs in the WSH installer at the command line.
Last I saw, WINE wasn't handling self-reg. DLLs."

Can someone please help me out with this? I'm stuck on step one lol..

---

### Post by Harlequin. on 2009-09-14
Please...

---

### Post by Harlequin. on 2009-09-14
For gods sake.. 

Anyway, I have to register the COM DLLs that came with WHS 5.6, but I don't know what they are, there is a sea of DLL files in my system32 folder..

---

### Post by Harlequin. on 2009-09-14
Thanks for nothing, I got it working myself.

---

### Post by NoaHall on 2009-09-14
Why are you so ungrateful ? You're asking on a Ubuntu forum about something that's coded in a Windows only language, and you expect us to answer. You haven't told us any error message, and no good description of the problem. The problem you seemed to have was answered in the first reply.

---

