---
title: "Can't get IrfanView to install under Wine on Karmic"
date: 2009-12-08
forum: General Help
---

### Post by kimharding on 2009-12-08
I had IrfanView installed under Wine on Jaunty but having upgraded(?) to Karmic in just can't get it to install at all. Each time I try I get the following error message, but I have got the mfc42.dll file in the wine system32 directory. Any ideas?


```

~$ wine iview425_setup.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:module:import_dll Library KERNELBASE.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Debug-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ErrorHandling-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-File-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Handle-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Interlocked-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-LibraryLoader-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Localization-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-LocalRegistry-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Memory-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Misc-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ProcessEnvironment-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ProcessThreads-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Profile-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-String-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Synch-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-SysInfo-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"H:\\iview425_setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\iview425_setup.exe" failed, status c0000135

```

---

### Post by howefield on 2009-12-08
From the wine website..

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

Additional comments.
* In order to install IrfanView 4.0 or newer versions you must have MFC42.DLL library (copy to system32 in .wine directory)

* Delete the i_view32.ini in IrfanView folder.

---

### Post by kimharding on 2009-12-08
Yes I do have the MFC42.DLL library in the system32 directory in the .wine directory. The program won't install so I don't have an IrfanView folder to Delete the i_view32.ini from...

---

### Post by Manyette on 2009-12-08
Don't know if you've ever tried Photofiltre, but it installs fine under Wine.  It's my favorite photo editor.

---

### Post by StuartN on 2009-12-08
> **Manyette said:**
> Don't know if you've ever tried Photofiltre, but it installs fine under Wine.  It's my favorite photo editor.

gThumb is very nice and it installs under Linux. Combine its lightweight facilities with a heavy duty editor under Edit With and you have a great solution.

---

### Post by Manyette on 2009-12-09
gThumb is better than any of the others I"ve found, but it isn't up to the features of Photofiltre.  Guess I'm just a photo editor bigot.:D

---

### Post by Jerry N on 2009-12-09
I have found Xnview to work better than Irfanview under Wine and Crossover.  Almost the same features.

---

### Post by mark bower on 2009-12-28
@kimharding

If you find a solution to your problem, please post here. I find that IrfanView works perfect for my needs on 9.04, but I am planning to move to 9.10.

---

