---
title: "Error in Synergy"
date: 2009-12-10
forum: General Help
---

### Post by LiaGalanodel on 2009-12-10
Hi everybody!

I have a big problem when I want to have two screen with one keyboard and one mouse.

I have two computer:
-Linux: Unbuntu 9.04 (server)
-Windows XP (client)

The name of windows computer is: windows
And the name of linux computer is: SorinLinux

 	Code:
 	root@SorinLinux:/home/amelieathanassiadis/workspace/Synergy# synergys -f --config /etc/synergy.conf
INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.28-16-generic #57-Ubuntu SMP Wed Nov 11 09:47:24 UTC 2009 i686
DEBUG: synergys.cpp,1051: opening configuration "/etc/synergy.conf"
DEBUG: synergys.cpp,1062: configuration read successfully
DEBUG: CXWindowsScreen.cpp,847: XOpenDisplay(":0.0")
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000
DEBUG: CXWindowsScreen.cpp,117: screen shape: 0,0 1680x1050 
DEBUG: CXWindowsScreen.cpp,118: window is 0x03c00004
DEBUG: CScreen.cpp,38: opened display
DEBUG: CXWindowsScreen.cpp,679: registered hotkey F12 (id=efc9 mask=0000) as id=1
NOTE: synergys.cpp,500: started server
INFO: CServer.cpp,1141: screen "SorinLinux" shape changed
NOTE: CClientListener.cpp,127: accepted client connection
DEBUG: CClientProxy1_0.cpp,404: received client "windows" info shape=0,0 1680x1050
NOTE: CServer.cpp,278: client "windows" has connected
NOTE: CClientProxy1_0.cpp,221: **client "windows" is dead** 
I don't understand the client is dead error.

Can you help me?

Thank you,

Best regards

---

### Post by LiaGalanodel on 2009-12-11
I try windows server and linux client but it doesn't work:

conncetion refused

---

### Post by undecim on 2009-12-11
Seems to me that it may be a network or firewall issue. Are these two machines on the same subnet? (i.e. connected to the same router)

Do you have any firewall software running on either computer?

---

### Post by LiaGalanodel on 2009-12-11
Yes I have the same router. 
My firewall are inactive.

---

