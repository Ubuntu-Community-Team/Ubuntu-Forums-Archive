---
title: "Pipe error on wine with wow?"
date: 2011-12-27
forum: General Help
---

### Post by haqzor7 on 2011-12-27
Hi all, I recently messed up my WoW.exe or something because as of late, if I try to play wow, my FPS lacks, and if I go to certain areas I DC, when I log back in, I get a memory error! Or sometimes I don't DC and just get the memory error! It says I don't have 2mb of ram, when I do, yea I know it's only a laptop, but I've never had problems before, I also get a bunch of pipe errors, I checked google for them, but the only fix I got, was this,
```

sudo bash
ulimit -n 10000
su $username

```
That made my problems worse, luckily it fixed when I closed that terminal, below is the entire list, from when I start wow, till I end it,
```
haqzor7@haqzor7-Ubuntu:~/.wine/drive_c/Program Files/Ubuntu Games/World of Warcraft3$ wine "wow.exe" --opengl
fixme:service:scmdatabase_autostart_services Auto-start service L"Apple Mobile Device" failed to start: 2
fixme:service:scmdatabase_autostart_services Auto-start service L"Bonjour Service" failed to start: 2
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
Unable to read extra attributes: "Data\enUS\patch-enUS-4.MPQ"
archive Data\enUS\patch-enUS-4.MPQ opened
Unable to read extra attributes: "Data\enUS\patch-enUS-5.mpq"
archive Data\enUS\patch-enUS-5.mpq opened
Unable to read extra attributes: "Data\enUS\patch-enUS-9.mpq"
archive Data\enUS\patch-enUS-9.mpq opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
Unable to read extra attributes: "Data\patch-4.MPQ"
archive Data\patch-4.MPQ opened
Unable to read extra attributes: "Data\patch-6.mpq"
archive Data\patch-6.mpq opened
Unable to read extra attributes: "Data\patch-D.MPQ"
archive Data\patch-D.MPQ opened
archive Data\Patch-G.mpq opened
Unable to read extra attributes: "Data\patch-I.MPQ"
archive Data\patch-I.MPQ opened
Unable to read extra attributes: "Data\Patch-P.MPQ"
archive Data\Patch-P.MPQ opened
archive Data\Patch-Q.mpq opened
archive Data\Patch-R.mpq opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x195ee20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195ecf4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f1cc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f464,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f5f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f1b4,0x00000000), stub!
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x195f9e4): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x195df60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195df88,0x00000000), stub!
fixme:ras:RasEnumConnectionsA (0x630607a8,0xd19e840,0x6305f610),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x195db28,0x00000000), stub!
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
failed to open C:/Program Files/Ubuntu Games/World of Warcraft3/Data/Interface/Icons
failed to open C:/Program Files/Ubuntu Games/World of Warcraft3/Interface/Icons
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x40020, 0x13ca10): stub
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
wine client error:3ce: pipe: Too many open files
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
wine client error:3da: pipe: Too many open files
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
err:mmdevapi:DllGetClassObject Driver initialization failed
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80004005
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x1
wine client error:3f2: pipe: Too many open files
wine client error:3f6: pipe: Too many open files
wine client error:3fa: pipe: Too many open files
wine client error:3fe: pipe: Too many open files
wine client error:402: pipe: Too many open files
fixme:win:EnumDisplayDevicesW ((null),0,0x195df68,0x00000000), stub!
wine client error:406: pipe: Too many open files
wine client error:40a: pipe: Too many open files
wine client error:40e: pipe: Too many open files
wine client error:412: pipe: Too many open files
wine client error:416: pipe: Too many open files
wine client error:41a: pipe: Too many open files
wine client error:41e: pipe: Too many open files
wine client error:422: pipe: Too many open files
wine client error:426: pipe: Too many open files
wine client error:42a: pipe: Too many open files
wine client error:42e: pipe: Too many open files
wine client error:432: pipe: Too many open files
wine client error:436: pipe: Too many open files
wine client error:43a: pipe: Too many open files
wine client error:43e: pipe: Too many open files
wine client error:442: pipe: Too many open files
wine client error:446: pipe: Too many open files
wine client error:44a: pipe: Too many open files
wine client error:2e2: pipe: Too many open files
wine client error:2ea: pipe: Too many open files
wine client error:2f2: pipe: Too many open files
wine client error:2fa: pipe: Too many open files
wine client error:302: pipe: Too many open files
wine client error:30a: pipe: Too many open files
wine client error:312: pipe: Too many open files
wine client error:31a: pipe: Too many open files
wine client error:322: pipe: Too many open files
wine client error:32a: pipe: Too many open files
wine client error:332: pipe: Too many open files
wine client error:33a: pipe: Too many open files
wine client error:342: pipe: Too many open files
wine client error:34a: pipe: Too many open files
wine client error:352: pipe: Too many open files
wine client error:35a: pipe: Too many open files
wine client error:362: pipe: Too many open files
wine client error:36a: pipe: Too many open files
wine client error:372: pipe: Too many open files
wine client error:37a: pipe: Too many open files
wine client error:382: pipe: Too many open files
wine client error:38a: pipe: Too many open files
wine client error:392: pipe: Too many open files
wine client error:39a: pipe: Too many open files
wine client error:3a2: pipe: Too many open files
wine client error:3aa: pipe: Too many open files
wine client error:3b2: pipe: Too many open files
wine client error:3ba: pipe: Too many open files
wine client error:3c2: pipe: Too many open files
wine client error:3ca: pipe: Too many open files
wine client error:3d2: pipe: Too many open files
wine client error:3da: pipe: Too many open files
wine client error:32: pipe: Too many open files
wine client error:31: pipe: Too many open files
wine client error:33: pipe: Too many open files
wine client error:3de: pipe: Too many open files
wine client error:3e6: pipe: Too many open files
wine client error:3f2: pipe: Too many open files
wine client error:3f6: pipe: Too many open files
wine client error:3fa: pipe: Too many open files
wine client error:3fe: pipe: Too many open files
wine client error:402: pipe: Too many open files
wine client error:406: pipe: Too many open files
wine client error:40a: pipe: Too many open files
wine client error:40e: pipe: Too many open files
wine client error:412: pipe: Too many open files
wine client error:416: pipe: Too many open files
wine client error:41a: pipe: Too many open files
wine client error:41e: pipe: Too many open files
wine client error:422: pipe: Too many open files
wine client error:426: pipe: Too many open files
wine client error:42a: pipe: Too many open files
wine client error:42e: pipe: Too many open files
wine client error:432: pipe: Too many open files
wine client error:436: pipe: Too many open files
wine client error:43a: pipe: Too many open files
wine client error:43e: pipe: Too many open files
wine client error:442: pipe: Too many open files
wine client error:446: pipe: Too many open files
wine client error:44a: pipe: Too many open files
wine client error:2e2: pipe: Too many open files
wine client error:2ea: pipe: Too many open files
wine client error:2f2: pipe: Too many open files
wine client error:2fa: pipe: Too many open files
wine client error:302: pipe: Too many open files
wine client error:30a: pipe: Too many open files
wine client error:312: pipe: Too many open files
wine client error:31a: pipe: Too many open files
wine client error:322: pipe: Too many open files
wine client error:32a: pipe: Too many open files
wine client error:332: pipe: Too many open files
wine client error:33a: pipe: Too many open files
wine client error:342: pipe: Too many open files
wine client error:34a: pipe: Too many open files
wine client error:352: pipe: Too many open files
wine client error:35a: pipe: Too many open files
wine client error:362: pipe: Too many open files
wine client error:36a: pipe: Too many open files
wine client error:372: pipe: Too many open files
wine client error:37a: pipe: Too many open files
wine client error:382: pipe: Too many open files
wine client error:38a: pipe: Too many open files
wine client error:392: pipe: Too many open files
wine client error:39a: pipe: Too many open files
wine client error:3a2: pipe: Too many open files
wine client error:3aa: pipe: Too many open files

```
I've tried google, and this is my last resort, any help would be appreciated

---

### Post by haqzor7 on 2011-12-27
I'm still kinda noob at forums, so if any additional info is needed, please ask and I will happily supply!

---

### Post by haqzor7 on 2011-12-27
Anyone? Any help or ideas would be tested, or did I post this in the wrong forum?

---

