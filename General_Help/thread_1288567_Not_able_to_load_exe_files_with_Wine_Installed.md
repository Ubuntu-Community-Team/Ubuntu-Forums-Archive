---
title: "Not able to load exe files with Wine Installed"
date: 2009-10-11
forum: General Help
---

### Post by HPspectre3 on 2009-10-11
hi, i installed wine 1.1.26 because it is more compatible with Runes of Magic wich i am trying to install. in applications i have wine - programs,browse C:/, configure Wine, and uninstal wine. in programs i only have notepad.
i Downloaded an exe with 6 .bin files to go with it, the exe extracts them and there you go as you probably know. also i imported MSpaint.exe from another computer with a CD, i get the error on that too. it seems all exe's. here is the error:

```
[/home/hpspectre3/Desktop/ROMSetup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/hpspectre3/Desktop/ROMSetup.exe or
          /home/hpspectre3/Desktop/ROMSetup.exe.zip, and cannot find /home/hpspectre3/Desktop/ROMSetup.exe.ZIP, period.
```my brother told me to go into the terminal and type something in to see what the problem might be. this is what i got:

```
hpspectre3@ubuntu:~$ cd Desktop
hpspectre3@ubuntu:~/Desktop$ wine mspaint.exe
err:module:import_dll Library MFC42u.DLL (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\mspaint.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\hpspectre3\\Desktop\\mspaint.exe" failed, status c0000135
hpspectre3@ubuntu:~/Desktop$ 
```can anyone tell me whats wrong? i really want to install this game.

---

### Post by HPspectre3 on 2009-10-11
btw, this sais this in Archive Manager if that helps

---

### Post by oldos2er on 2009-10-11
```
wine ~/Desktop/ROMSetup.exe
``` should work.

---

### Post by HPspectre3 on 2009-10-11
thanks i think is installed. but when i try to run the program i get this error

```
fixme:shell:DllCanUnloadNow stub
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:shell:DllCanUnloadNow stub
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Runes of Magic\\xerces-c_2_8.dll") not found
err:module:import_dll Library xerces-c_2_8.dll (which is needed by L"C:\\Program Files\\Runes of Magic\\Client.exe") not found
hpspectre3@ubuntu:~/Desktop$ err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Runes of Magic\\Client.exe" failed, status c0000135
```

sorry for the big post, im just not sure whats important.
any idea what this means?

---

### Post by oldos2er on 2009-10-14
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16051](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16051)

Some Win* apps just won't work in Wine.

---

