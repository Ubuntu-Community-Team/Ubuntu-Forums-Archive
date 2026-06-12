---
title: "ffado und jackd per script laden"
date: 2009-09-12
forum: General Help
---

### Post by leyla on 2009-09-12
Hi there! I stumbled upon a small problem:

My Firewire Audio-Interface "Focusrite Saffire LE" works fine after starting ffado and jackd manually. Now I its time to get them started automatically at the beginning of every ubuntu session via script. The script looks like this right now:

------------------------------------
#!/bin/sh

ffado-dbus-server &

sleep 10

jackd -R -d firewire -n 3 -p 2048 &

exit 0
-----------------------------------

If I start this script manually, it doesnt work. If I start the script again a second time right after the first time, it works. 
Why at the second try not on the first? My weak solution now is to duplicate script content to emulate a second try. Its working but I want to have a proper solution and also to understand whats going on. 

Heres the log which is given to me everytime after first try starting the script: 



leyla@studio:~$ /etc/init.d/focusrite
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

00428907534:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
00428909998: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00429016852: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
00429016920: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193392910 (0x7FC80000130E)
00429016960: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7FC800000000)
00429016996: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Focusrite
00429017029: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Saffire (LE)
00429017062: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388033 (0x7FC800000001)
00429017098: Debug (Configuration.cpp)[ 208] showSetting:     mixer = SaffireMixer
00429017308: Debug (devicemanager.cpp)[ 594] discover: driver found for device 1
00429035348: Debug (bebob_avdevice.cpp)[ 734] loadFromCache: filename /home/leyla/.ffado/cache/00130e01000433b7/000000fffe070904.xml
00429035404: Debug (bebob_avdevice.cpp)[ 738] loadFromCache: "/home/leyla/.ffado/cache/00130e01000433b7/000000fffe070904.xml" does not exist
00429035477: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
00429035512: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193392910 (0x7FC80000130E)
00429035546: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7FC800000000)
00429035579: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Focusrite
00429035615: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Saffire (LE)
00429035648: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388033 (0x7FC800000001)
00429035682: Debug (Configuration.cpp)[ 208] showSetting:     mixer = SaffireMixer
00429038011: Debug (bebob_avdevice_subunit.cpp)[  83] discover: Discovering BeBoB::AudioSubunit...
00429038053: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering BeBoB::AudioSubunit...
00429038087: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00429201393: Debug (bebob_avdevice_subunit.cpp)[ 132] discoverFunctionBlocks: Discovering function blocks...
00429215139: Debug (bebob_avdevice_subunit.cpp)[ 449] discover: Discovering BeBoB::MusicSubunit...
00429215187: Debug (avc_musicsubunit.cpp)[  64] discover: Discovering BeBoB::MusicSubunit...
00429215220: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00429952987: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
00429956116: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 2
00429956171: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 2
00429956203: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 5
00429956234: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 5
00429956264: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
00430065566: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Compound Input' found
00430106953: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Synch Input' found
00430106975: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
00430198084: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Compound Output' found
00430237060: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Synch Output' found
00430237102: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
00430283209: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Midi Input' found
00430332734: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'SPDIF Input' found
00430382365: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Input 1/2' found
00430432076: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Input 3/4' found
00430472028: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'SPDIF Input Sync' found
00430472049: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
00430520276: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Midi Output' found
00430572021: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'SPDIF Output' found
00430621903: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Output 1/2' found
00430671749: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Output 3/4' found
00430721245: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Output 5/6' found
00430721293: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
00430747420: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
00430814248: Debug (bebob_avdevice_subunit.cpp)[ 102] discoverConnections: Discovering connections...
00430814272: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00430867218: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00430977432: Debug (avc_unit.cpp)[ 843] checkSyncConnectionsAndAddToList: Internal (CSP), sync connection 'Internal Sync' -> 'MSU Synch Input'
00430980120: Debug (avc_unit.cpp)[ 843] checkSyncConnectionsAndAddToList: Digital Input Sync, sync connection 'SPDIF Input Sync' -> 'MSU Synch Input'
00430998268: Error (bebob_avdevice.cpp)[ 794] saveCache: Could not create "/home/leyla/.ffado/cache" directory
00430998340: Debug (devicemanager.cpp)[ 631] discover: discovery of node 1 on port 0 done...
00430998375: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00430998454: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
00430998492: Debug (Element.cpp)[ 121] show: Element DeviceManager
00430998524: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00430998653: Debug (devicemanager.cpp)[1105] showDeviceInfo: --- Device  0 ---
00430998684: Debug (focusrite_saffire.cpp)[ 398] showDevice: This is a BeBoB::Focusrite::SaffireDevice (Saffire LE)
00430998716: Debug (focusrite_generic.cpp)[  44] showDevice: This is a BeBoB::Focusrite::FocusriteDevice
00430998751: Debug (bebob_avdevice.cpp)[ 480] showDevice: Device is a BeBoB device
00430998788: Debug (ffadodevice.cpp)[ 224] showDevice: Attached to port.......: 0 (ohci1394)
00430998819: Debug (ffadodevice.cpp)[ 225] showDevice: Node...................: 1
00430998851: Debug (ffadodevice.cpp)[ 227] showDevice: Vendor name............: Focusrite
00430998886: Debug (ffadodevice.cpp)[ 229] showDevice: Model name.............: SaffireLE
00430998919: Debug (ffadodevice.cpp)[ 231] showDevice: GUID...................: 00130e01000433b7
00430998957: Debug (ffadodevice.cpp)[ 236] showDevice: Assigned ID....: dev0
00430998990: Debug (devicemanager.cpp)[1108] showDeviceInfo: Clock sync sources:
00430999061: Debug (avc_unit.cpp)[ 815] getActiveSyncInfo: Active Sync Connection: Internal (CSP), 'Internal Sync' -> 'MSU Synch Input'
00430999121: Debug (avc_unit.cpp)[ 815] getActiveSyncInfo: Active Sync Connection: Internal (CSP), 'Internal Sync' -> 'MSU Synch Input'
00430999163: Debug (devicemanager.cpp)[1117] showDeviceInfo:  Type: Internal          , Id: 20, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal (CSP)
00430999200: Debug (devicemanager.cpp)[1117] showDeviceInfo:  Type: SPDIF             , Id: 29, Valid: 1, Active: 0, Locked 1, Slipping: 0, Description: SPDIF Input Sync
00430999260:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
00431014630:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
00431014658: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
leyla@studio:~$ no message buffer overruns
jackd 0.116.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
00438938985:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Sep 12 2009 02:09:03
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
00442106488: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x1f879d0...
00442106511: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
00442106520: Debug (devicemanager.cpp)[ 242] busresetHandler: issue busreset on device GUID 00130e01000433b7
00443106577: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443107681: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443108791: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443109894: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443111055: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443113134: Warning (configrom.cpp)[ 504] updatedNodeId: Failed to get/parse CSR
00443120300: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
00443147852: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00443147962: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443149074: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443150192: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443151305: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443152412: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443154530: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
00443154542: Debug (devicemanager.cpp)[ 376] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
00443154548: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
00443154937: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
00443165452: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443166568: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443167680: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443168803: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443169929: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443172050: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
00443172059: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
00443172064: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00443172067: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
00443172075: Debug (Element.cpp)[ 121] show: Element DeviceManager
00443172078: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00443172096: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...
00443172136: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
00443172140: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
00443173292: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x1f879d0...
00443173297: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
00443173300: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
00443197905: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00443198107: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443199187: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443200467: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443201641: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443202757: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443204874: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
00443204881: Debug (devicemanager.cpp)[ 376] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
00443204888: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
00443204975: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443206084: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443207187: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443208297: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443209423: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
00443211539: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
00443211544: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
00443211547: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00443211553: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
00443211556: Debug (Element.cpp)[ 121] show: Element DeviceManager
00443211558: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00443211578: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...
00446212771: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x1f879d0...
00446212790: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
00446212794: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
00446243460: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00446296249: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
00446369752: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
00446369764: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140496970191630 (0x7FC80000130E)
00446369767: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140496970186752 (0x7FC800000000)
00446369770: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Focusrite
00446369781: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Saffire (LE)
00446369784: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140496970186753 (0x7FC800000001)
00446369786: Debug (Configuration.cpp)[ 208] showSetting:     mixer = SaffireMixer
00446369855: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
00446387776: Debug (bebob_avdevice.cpp)[ 734] loadFromCache: filename /home/leyla/.ffado/cache/00130e01000433b7/000000fffe070904.xml
00446387789: Debug (bebob_avdevice.cpp)[ 738] loadFromCache: "/home/leyla/.ffado/cache/00130e01000433b7/000000fffe070904.xml" does not exist
00446387822: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
00446387825: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140496970191630 (0x7FC80000130E)
00446387833: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140496970186752 (0x7FC800000000)
00446387837: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Focusrite
00446387839: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Saffire (LE)
00446387841: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140496970186753 (0x7FC800000001)
00446387847: Debug (Configuration.cpp)[ 208] showSetting:     mixer = SaffireMixer
00446390740: Debug (bebob_avdevice_subunit.cpp)[  83] discover: Discovering BeBoB::AudioSubunit...
00446390745: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering BeBoB::AudioSubunit...
00446390748: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00446555181: Debug (bebob_avdevice_subunit.cpp)[ 132] discoverFunctionBlocks: Discovering function blocks...
00446568104: Debug (bebob_avdevice_subunit.cpp)[ 449] discover: Discovering BeBoB::MusicSubunit...
00446568110: Debug (avc_musicsubunit.cpp)[  64] discover: Discovering BeBoB::MusicSubunit...
00446568113: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00447265119: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
00447268012: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 2
00447268047: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 2
00447268079: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 5
00447268116: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 5
00447268147: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
00447365212: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Compound Input' found
00447400391: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Synch Input' found
00447400417: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
00447479835: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Compound Output' found
00447514772: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Synch Output' found
00447514791: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
00447555627: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Midi Input' found
00447600028: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'SPDIF Input' found
00447644539: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Input 1/2' found
00447688962: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Input 3/4' found
00447724065: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'SPDIF Input Sync' found
00447724089: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
00447765082: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Midi Output' found
00447809557: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'SPDIF Output' found
00447854192: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Output 1/2' found
00447899026: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Output 3/4' found
00447943615: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'Analog Output 5/6' found
00447943636: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
00447967504: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
00448027657: Debug (bebob_avdevice_subunit.cpp)[ 102] discoverConnections: Discovering connections...
00448027676: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00448075480: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00448174929: Debug (avc_unit.cpp)[ 843] checkSyncConnectionsAndAddToList: Internal (CSP), sync connection 'Internal Sync' -> 'MSU Synch Input'
00448177317: Debug (avc_unit.cpp)[ 843] checkSyncConnectionsAndAddToList: Digital Input Sync, sync connection 'SPDIF Input Sync' -> 'MSU Synch Input'
00448193310: Error (bebob_avdevice.cpp)[ 794] saveCache: Could not create "/home/leyla/.ffado/cache" directory
00448193835: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
00448193848: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
00448193850: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
00448208598: Debug (devicemanager.cpp)[ 631] discover: discovery of node 0 on port 0 done...
00448208620: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00448208654: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
00448208657: Debug (Element.cpp)[ 121] show: Element DeviceManager
00448208659: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00448208674: Debug (devicemanager.cpp)[1105] showDeviceInfo: --- Device  0 ---
00448208676: Debug (focusrite_saffire.cpp)[ 398] showDevice: This is a BeBoB::Focusrite::SaffireDevice (Saffire LE)
00448208681: Debug (focusrite_generic.cpp)[  44] showDevice: This is a BeBoB::Focusrite::FocusriteDevice
00448208683: Debug (bebob_avdevice.cpp)[ 480] showDevice: Device is a BeBoB device
00448208685: Debug (ffadodevice.cpp)[ 224] showDevice: Attached to port.......: 0 (ohci1394)
00448208688: Debug (ffadodevice.cpp)[ 225] showDevice: Node...................: 0
00448208692: Debug (ffadodevice.cpp)[ 227] showDevice: Vendor name............: Focusrite
00448208693: Debug (ffadodevice.cpp)[ 229] showDevice: Model name.............: SaffireLE
00448208696: Debug (ffadodevice.cpp)[ 231] showDevice: GUID...................: 00130e01000433b7
00448208700: Debug (ffadodevice.cpp)[ 236] showDevice: Assigned ID....: dev0
00448208743: Debug (devicemanager.cpp)[1108] showDeviceInfo: Clock sync sources:
00448208766: Debug (avc_unit.cpp)[ 815] getActiveSyncInfo: Active Sync Connection: Internal (CSP), 'Internal Sync' -> 'MSU Synch Input'
00448208778: Debug (avc_unit.cpp)[ 815] getActiveSyncInfo: Active Sync Connection: Internal (CSP), 'Internal Sync' -> 'MSU Synch Input'
00448208783: Debug (devicemanager.cpp)[1117] showDeviceInfo:  Type: Internal          , Id: 20, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal (CSP)
00448208791: Debug (devicemanager.cpp)[1117] showDeviceInfo:  Type: SPDIF             , Id: 29, Valid: 1, Active: 0, Locked 1, Slipping: 0, Description: SPDIF Input Sync
00448208798: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...



Thanks in advance!

---

