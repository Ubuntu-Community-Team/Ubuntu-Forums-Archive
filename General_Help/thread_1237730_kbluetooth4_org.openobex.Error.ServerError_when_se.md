---
title: "kbluetooth4 org.openobex.Error.ServerError when sending files"
date: 2009-08-11
forum: General Help
---

### Post by khamil8686 on 2009-08-11
I put in my bluetooth adapter and KBluetooth4 program pops up in the tray, i try to send a file and it gets to about 14% or 32% and then gives me a org.openobex.Error.ServerError error and stops sending the file. i tried running kbluetooth4 from the command line so i could see output of the program when it has this error but i cant make sense of what could be wrong. heres the output:

```

~$ kbluetooth4
kbluetooth4(29708) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "BlueZ"         
kbluetooth4(29708) Solid::Control::BluetoothManager::buildDeviceList: UBI List  ("/org/bluez/2949/hci0")                                                                                                  
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: findRegisteredBluetoothInterface  "/org/bluez/2949/hci0"                                                    
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: Creating New Interface  "/org/bluez/2949/hci0"                                                              
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: Calling Backend to Creating New Interface  "/org/bluez/2949/hci0"                                           
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: BackendIface created
kbluetooth4(29708) BluezBluetoothManager::defaultInterface: Calling Backend Default Interface
kbluetooth4(29708) KBlueTray::onlineMode: online Mode
kbluetooth4(29708) Solid::Control::BluetoothManager::buildDeviceList: UBI List  ("/org/bluez/2949/hci0")
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: findRegisteredBluetoothInterface  "/org/bluez/2949/hci0"
kbluetooth4(29708) KBlueTray::onlineMode: adapter size  1
kbluetooth4(29708) BluezBluetoothManager::defaultInterface: Calling Backend Default Interface
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: findRegisteredBluetoothInterface  "/org/bluez/2949/hci0"
kbluetooth4(29708) KBlueTray::onlineMode: Adapter found  "khamil8686-desktop-0"
kbluetooth4(29708) BluezBluetoothManager::defaultInterface: Calling Backend Default Interface
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: findRegisteredBluetoothInterface  "/org/bluez/2949/hci0"
AGENT registered !
kbluetooth4(29708) ObexServer::ObexServer: "00:00:00:00:00:00"
kbluetooth4(29708) ObexServer::serverCreated: obex server created
kbluetooth4(29708) ObexServer::serverCreated: session interface created for:  "/org/openobex/server3"
kbluetooth4(29708) ObexServer::slotStarted: server started
kbluetooth4(29708) KBlueTray::slotServerStarted: obex server started
~$ kbluetooth4(29708) BluezBluetoothManager::defaultInterface: Calling Backend Default Interface
kbluetooth4(29708) Solid::Control::BluetoothManagerPrivate::findRegisteredBluetoothInterface: findRegisteredBluetoothInterface  "/org/bluez/2949/hci0"
kbluetooth4(29708) BluezBluetoothInterface::slotDeviceFound: device found  "00:1E:75:EA:15:4B"   QVariant(QString, "Yoshi")
Remote Device found  "00:1E:75:EA:15:4B" Name:  QVariant(QString, "Yoshi")
kbluetooth4(29708) ObexSession::ObexSession: Konstruktor:  "/org/openobex"
kbluetooth4(29708) ObexSession::sessionCreated: session interface created for:  "/org/openobex/session3"
kbluetooth4(29708) KBlueTray::obexSessionReady: is connected:  false
kbluetooth4(29708) KBlueTray::slotFileSendStarted: file send started:  "/home/khamil8686/Desktop/334px-Tux.svg.png" "334px-Tux.svg.png"
kbluetooth4(29708) KBlueTray::slotFileSendStarted: size:  113476
kbluetooth4(29708) KBlueTray::slotTransferProgress: Transfered:  15944
kbluetooth4(29708) KBlueTray::slotTransferProgress: Progress:  14
kbluetooth4(29708) KBlueTray::slotServerErrorOccured: "org.openobex.Error.ServerError" :  "Remote server error"
```

i dont see any specific errors or anything, only thing i noticed that i dont know if it would cause an error or not was the obex server was created with an address of 00:00:00:00:00
bluetooth works fine in GNOME, and i can get the GNOME bluetooth application to work in kde, would just rather use the default KDE bluetooth application because when i put in my bluetooth adapter kbluetooth4 pops up, would be a hassle to launch the gnome application.
also i can recieve files fine from my phone, a LG UX260
any help would be appreciated :)

---

### Post by khamil8686 on 2009-08-15
some kinda problem with kbluetooth4 i guess. cuz i can send files just fine using the command line obexftp

---

