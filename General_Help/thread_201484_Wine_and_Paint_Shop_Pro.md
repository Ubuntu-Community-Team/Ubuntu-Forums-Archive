---
title: "Wine and Paint Shop Pro"
date: 2006-06-21
forum: General Help
---

### Post by Etoile on 2006-06-21
I have configured wine to use my existing XP partition, which I mounted into Ubuntu, by setting the C: drive to be where my partition is mounted.  The wine config seems fine as most basic apps (Notepad, Solitaire) work well.  But when I go to start Paint Shop Pro (PSP9) I get the following dialog box:
> The folder below is used to save your user files.  It is not currently accessible.

C:\Program Files\Paint Shop Pro 9\

Check whether your user file folder is on a network or on a drive that is no longer accessible.  If so, Cancel and reconnect to the drive or network and run Paint Shop Pro again.

If the folder listed above no longer exists or has been renamed or moved, please specify an emergency read/write directory by pressing OK.

When Paint Shop Pro launches you must reconfigure your file locations by selecting:
File - Preferences - File Locations
When I select Okay, I get the following box:
> Browse for Folder
Please choose a default user save directory
There is nothing listed for me to choose as a default user save directory.

Here's what's going on in Terminal meanwhile:
```
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:ole:CoRegisterMessageFilter stub
fixme:mlang:fnIMultiLanguage_GetRfc1766Info
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\Desktop"'.
err:heap:HEAP_ValidateInUseArena Heap 0x7fcf0000: in-use arena 0x7fd833d0 next block has PREV_FREE flag
fixme:ole:CoRegisterMessageFilter stub
```

Does anyone have suggestions?  I'm new to Ubuntu and even newer to wine, so I'm at a loss!  (Though I'm not new to geekery in general, so I will probably understand what you tell me.)

---

### Post by rai4shu2 on 2006-06-21
Wine should really use the "~/.wine/drive_c" folder as the location of C: (anything else can cause problems).

---

### Post by Etoile on 2006-06-21
[QUOTE=rai4shu2]Wine should really use the "~/.wine/drive_c" folder as the location of C: (anything else can cause problems).[/QUOTE]
No matter what I try to set Drive C to be, I get this in the Terminal window:
```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\My Documents"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\My Pictures"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\My Music"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\My Video"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\meredith\\Desktop"'.
```
I recognize these from the Desktop Integration tab in winecfg, but I seem to be unable to click "Link to" for any of these entries.  (And that isn't the correct setup for XP anyway, shouldn't it be C:\Documents and Settings\Meredith\My Documents etc.?)

---

