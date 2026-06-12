---
title: "Wine Errors"
date: 2006-06-17
forum: General Help
---

### Post by Cable on 2006-06-17
I'm getting some errors in Wine.

1)  When I click "Add Application" in the Applications tab of winecfg, no drives show up in the drop down drive list at the top.  I have set it to auto detect drives, so it knows drives are there.  The list is just completely empty, so I can't browse to any .exe's or anything.  Once I click on the drop down menu, it sort of freezes, exits, then throws a bunch of errors in the terminal.  Here they are...
```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f9c491d (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7f9c491d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7f9c491d ESP:7fb4dda0 EBP:7fb4ddc8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7f9e53c8 ECX:7fce0020 EDX:00000000
 ESI:7fb4ef2c EDI:ffffffff
Stack dump:
0x7fb4dda0:  7fd44b18 7f9df32d 00000000 00000000
0x7fb4ddb0:  7fa3f3ac 00010044 7fb4ef2c 7f9e53c8
0x7fb4ddc0:  00000002 7fa3e8f4 7fb4de48 7f9c95cc
0x7fb4ddd0:  00010044 7f9df32d 00010044 7f9e53c8
0x7fb4dde0:  00000006 00000047 7fb4e108 7f9c9c2d
0x7fb4ddf0:  00010048 7f9df321 7fb4ded8 00010044
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7f9c491d in comdlg32 (+0x1491d) (0x7f9c491d)
  2 0x7f9c95cc in comdlg32 (+0x195cc) (0x7f9c95cc)
  3 0x7f9c9e70 FileOpenDlgProc95+0x6df in comdlg32 (0x7f9c9e70)
  4 0x7f71794a WINPROC_wrapper+0x1a in user32 (0x7f71794a)
  5 0x7f71806b WINPROC_wrapper+0x73b in user32 (0x7f71806b)
  6 0x7f71c51b in user32 (+0x9c51b) (0x7f71c51b)
  7 0x7f71ce70 WINPROC_CallDlgProcW+0xae in user32 (0x7f71ce70)
  8 0x7f6b09f7 DefDlgProcW+0x84 in user32 (0x7f6b09f7)
  9 0x7f71794a WINPROC_wrapper+0x1a in user32 (0x7f71794a)
  10 0x7f719853 in user32 (+0x99853) (0x7f719853)
  11 0x7f71cf0c CallWindowProcW+0x57 in user32 (0x7f71cf0c)
  12 0x7f6e6cc6 in user32 (+0x66cc6) (0x7f6e6cc6)
  13 0x7f6ea6d0 SendMessageTimeoutW+0x191 in user32 (0x7f6ea6d0)
  14 0x7f6ea72f SendMessageW+0x50 in user32 (0x7f6ea72f)
  15 0x7f69880b in user32 (+0x1880b) (0x7f69880b)
  16 0x7f6992bb in user32 (+0x192bb) (0x7f6992bb)
  17 0x7f71794a WINPROC_wrapper+0x1a in user32 (0x7f71794a)
  18 0x7f719853 in user32 (+0x99853) (0x7f719853)
  19 0x7f71cf0c CallWindowProcW+0x57 in user32 (0x7f71cf0c)
  20 0x7f6e705c DispatchMessageW+0x169 in user32 (0x7f6e705c)
  21 0x7f6b537b IsDialogMessageW+0xfb in user32 (0x7f6b537b)
  22 0x7f6b5c90 DIALOG_DoDialogBox+0x13b in user32 (0x7f6b5c90)
  23 0x7f6b7938 DialogBoxIndirectParamAorW+0x5a in user32 (0x7f6b7938)
  24 0x7f6b79d1 DialogBoxIndirectParamA+0x41 in user32 (0x7f6b79d1)
  25 0x7f9c3051 in comdlg32 (+0x13051) (0x7f9c3051)
  26 0x7f9c5365 GetFileDialog95A+0x4ce in comdlg32 (0x7f9c5365)
  27 0x7f9c54b6 GetOpenFileNameA+0x4b in comdlg32 (0x7f9c54b6)
  28 0x7fb710d1 AppDlgProc+0x963 in winecfg (0x7fb710d1)
  29 0x7f71794a WINPROC_wrapper+0x1a in user32 (0x7f71794a)
  30 0x7f71806b WINPROC_wrapper+0x73b in user32 (0x7f71806b)
  31 0x7f71ce19 WINPROC_CallDlgProcW+0x57 in user32 (0x7f71ce19)
  32 0x7f6b09f7 DefDlgProcW+0x84 in user32 (0x7f6b09f7)
  33 0x7f71794a WINPROC_wrapper+0x1a in user32 (0x7f71794a)
  34 0x7f719853 in user32 (+0x99853) (0x7f719853)
  35 0x7f71cf0c CallWindowProcW+0x57 in user32 (0x7f71cf0c)
  36 0x7f6e6cc6 in user32 (+0x66cc6) (0x7f6e6cc6)
  37 0x7f6ea6d0 SendMessageTimeoutW+0x191 in user32 (0x7f6ea6d0)
  38 0x7f6ea72f SendMessageW+0x50 in user32 (0x7f6ea72f)
  39 0x7f69880b in user32 (+0x1880b) (0x7f69880b)
  40 0x7f6992bb in user32 (+0x192bb) (0x7f6992bb)
  41 0x7f71794a WINPROC_wrapper+0x1a in user32 (0x7f71794a)
  42 0x7f719853 in user32 (+0x99853) (0x7f719853)
  43 0x7f71cf0c CallWindowProcW+0x57 in user32 (0x7f71cf0c)
  44 0x7f6e705c DispatchMessageW+0x169 in user32 (0x7f6e705c)
  45 0x7f6b537b IsDialogMessageW+0xfb in user32 (0x7f6b537b)
  46 0x7f3f9865 in comctl32 (+0x49865) (0x7f3f9865)
  47 0x7f3fd396 PropertySheetW+0x25a in comctl32 (0x7f3fd396)
  48 0x7fb798b3 WinMain+0x356 in winecfg (0x7fb798b3)
  49 0x7fb7e947 main+0xa7 in winecfg (0x7fb7e947)
  50 0x7fb7e883 in winecfg (+0x1e883) (0x7fb7e883)
  51 0x7fc4b94f in kernel32 (+0x4b94f) (0x7fc4b94f)
  52 0xb7f0c2e3 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f0c2e3)
0x7f9c491d: movl        0x0(%eax),%edx
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]
```
Then, when I exit the frozen winecfg, it does this...
```

wineserver: could not save registry branch to /home/caleb/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/caleb/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/caleb/.wine/user.reg : Permission denied

```

2)  When I go to the drives tab and click "Browse" next to the path line for *any* drive letter, the program does nothing and the terminal says this...
```

err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'G:\' failed, setting serial to 0
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\caleb\\Desktop"'.

```

What do I do to get Wine working corrrectly?

---

### Post by s_h_a_d_o_w_s on 2006-06-17
How did you get wine? Through automatix?

---

### Post by Cable on 2006-06-17
Through the repos.

---

