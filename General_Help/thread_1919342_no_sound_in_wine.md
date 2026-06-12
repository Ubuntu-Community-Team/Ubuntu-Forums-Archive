---
title: "no sound in wine"
date: 2012-02-02
forum: General Help
---

### Post by rogerdv on 2012-02-02
Im having a problem with wine since I installed Oneiric: wine cant initialize sound. this is the error in winecfg:

```
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\mmdevapi.dll"
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1

```

It worked perfectly in Ubuntu 11.04 and also, the sound works for the rest of the system. Any idea about whats happening?

---

### Post by BC59 on 2012-02-02
If you don't have it already, try installing the latest Wine.
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get install wine1.3
```
This way is installed the Wine 1.4rc1 (and not Wine 1.3)

---

### Post by lechien73 on 2012-02-02
Hi,

This is more to do with an update to Wine, rather than Ubuntu 11.10. Lots of users are having issues with this error, since Wine changed the libraries used for sound.

First try checking that the mmdevapi.dll file exists in the ~/.wine/drive_c/windows/system32 directory.

If it does, then you could try checking in winecfg to make sure the library isn't disabled (this can be the case if you've used winetricks). Click on the **Libraries** tab (as in the attached screenshot). If you see mmdevapi.dll listed in the **Existing Overrides** section, then remove it and try again.

---

### Post by rogerdv on 2012-02-02
Thanks! Indeed it was listed as disabled. Now it works.

---

### Post by lechien73 on 2012-02-02
You're welcome :)

If you get chance, please could you use the **Thread Tools** menu and mark the issue as [SOLVED]?

Many thanks,

---

