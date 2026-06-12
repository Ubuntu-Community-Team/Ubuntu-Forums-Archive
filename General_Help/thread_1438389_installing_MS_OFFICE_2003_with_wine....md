---
title: "installing MS OFFICE 2003 with wine..."
date: 2010-03-24
forum: General Help
---

### Post by jfca283 on 2010-03-24
hello
i'm trying to install office 2003, but i get a lot of errors
```
juan@joker:~/Desktop$ wine Office2003SP3.exe 
C:\windows\temp\7zS17a.tmp>cmdow.exe @ /HID
File not found

C:\windows\temp\7zS17a.tmp>copy OGACheckControl.dll c:\Windows\System32\OgaCheckControl.dll /Y
C:\windows\temp\7zS17a.tmp>setup.exe TRANSFORMS=UnattendedOT.MST /qb /noreboot
fixme:imm:ImmDisableIME (-1): stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 4/04/2010, dlt (d/m/y): 10/10/2010
fixme:advapi:CheckTokenMembership ((nil) 0x133e68 0x336d3c) stub!
fixme:advapi:LookupAccountNameW (null) L"juan" (nil) 0x33f864 (nil) 0x33f868 0x33f85c - stub
fixme:advapi:LookupAccountNameW (null) L"juan" 0x9c6c18 0x33f864 0x9c7588 0x33f868 0x33f85c - stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 4/04/2010, dlt (d/m/y): 10/10/2010
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 76 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented

fixme:msxml:DllCanUnloadNow 

fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 76 ignored L"Upgrade" table values
fixme:msi:ITERATE_PublishAssembly Manifest unhandled
fixme:mscoree:LoadLibraryShim (0x63f925b8 L"fusion.dll", (nil), (nil), 0x33f988): semi-stub
fixme:fusion:IAssemblyCacheImpl_InstallAssembly Ignoring assembly architecture!
fixme:msi:ITERATE_PublishAssembly Manifest unhandled
fixme:mscoree:LoadLibraryShim (0x63f925b8 L"fusion.dll", (nil), (nil), 0x33f988): semi-stub
fixme:fusion:IAssemblyCacheImpl_InstallAssembly Ignoring assembly architecture!
fixme:msi:ITERATE_PublishAssembly Manifest unhandled
fixme:mscoree:LoadLibraryShim (0x63f925b8 L"fusion.dll", (nil), (nil), 0x33f988): semi-stub
fixme:fusion:IAssemblyCacheImpl_InstallAssembly Ignoring assembly architecture!
fixme:msi:ITERATE_PublishAssembly Manifest unhandled

err:msi:ITERATE_PublishAssembly Failed to copy temporary assembly: 2

err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1627

C:\windows\temp\7zS17a.tmp>EXIT
```
is there a bug?
i've been searching and all installations were made with 1 or 2 commands
well...that's it
i only need to run excel with VBA support...the rest i do it with openoffice 
thanks

---

### Post by technoholic on 2010-03-25
I dont claim to be an expert but I have had success running XP in Virtual Box and installing Office there, might be worth a try. I am not sure of your VBA requirements however.

---

### Post by eperamak on 2010-04-05
I've not tried this yet (waiting for my SSD to arrive before re-installing 9.10 and ignoring XP again), but it looks promising. Seems to be WINE version-dependant...

[http://www.youtube.com/watch?v=-zYnZHb9Igc](http://www.youtube.com/watch?v=-zYnZHb9Igc)

---

