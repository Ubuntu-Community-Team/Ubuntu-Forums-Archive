---
title: "Lotro FAIL"
date: 2010-05-08
forum: General Help
---

### Post by xtremesupremacy3 on 2010-05-08
Ok so heres my problem.

I had Ubuntu Lucid beta 2 and had installed Lord of the rings online with pylotro which worked brilliant. But due to some problems with lucid i decided to reformat. So all said and done, I installed wine, winetricks, all the necesary files and went to install lotro...that went brilliantly, set up pylotro that was fine, patched and just to be sure also installed the CLI client of lotro.

Now when i start the client, it loads up everything so I can select realm, enter user name and password I select to login...that goes well...my screen changes resolution, the screen goes black...then...poof...it closes.

Here are the results I get on both pylotro and the CLI installer...can anyone make any sense of the reason behind the crash?

PyLOTRO:
```
bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

fixme:win:EnumDisplayDevicesW ((null),0,0x32f564,0x00000000), stub!

fixme:wbemprox:wbem_locator_ConnectServer 0x164378, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32fa74)

fixme:wbemprox:wbem_locator_ConnectServer 0x1657b8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32fa74)
fixme:wbemprox:wbem_locator_ConnectServer 0x1657b8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32facc)
fixme:advapi:RegisterTraceGuidsW (0x48024d0, 0x480d6e8, {7c830ece-5fb3-417a-a1bd-508f45277356}, 1, 0x2abe724, (null), (null), 0x480d6f0,)

fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table

fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x165f98) : stub

fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30052 0x00000000

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x9d1fdf0,0x9d1fd78): stub

bt_audio_service_open: connect() failed: Connection refused (111)

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

*** Finished ***
```

And for CLI:

```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
./lotrolauncher.sh: line 340:  2125 Segmentation fault      WINEDEBUG=fixme-all wine ${gameClient_FILE} ${gameClient_ARGS} $@

```

Please note that the 'bt_audio_service_open' error was there even when the game was working so I am not too fussed about that part.

Thanks for your help

---

### Post by xtremesupremacy3 on 2010-05-08
So i have managed to reduce the number of bad errors to simply 1:

```
wine-extension-vcproj.desktop": "Application/xml" is an invalid MIME type ("Application" is an unregistered media type)
```

I have no idea what this means, anyone understand it?

---

### Post by xtremesupremacy3 on 2010-05-08
ok so all errors gone, having tried once more it still failed. I checked the logs and im finally finding the culprit:

```
lotroclient.exe[18687]: segfault at 7b9b2f40 ip 7b9b2f40 sp aa8fbf9c error 4 in ntdll.dll.so
```

anyone able to explain what i can do to fix this?

---

### Post by xtremesupremacy3 on 2010-05-10
Okay, so the problem is now fixed.

Strangely enough, pulseaudio was the culprit.

After removing it, all went well

---

