---
title: "synergy help"
date: 2011-12-01
forum: General Help
---

### Post by inmate#001 on 2011-12-01
I'm Trying to set up synergy from my ubuntu 10.04 x64 desktop to my macbook with my ubuntu computer as the server however ever time i start synergy in debug mode i get a simmilar output in the terminal and I have no idea what the problem is please help


INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64
DEBUG: synergys.cpp,1051: opening configuration ".quicksynergy/synergy.conf"
DEBUG: synergys.cpp,1062: configuration read successfully
DEBUG: CXWindowsScreen.cpp,847: XOpenDisplay(":0.0")
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000
DEBUG: CXWindowsScreen.cpp,117: screen shape: 0,0 1440x900 
DEBUG: CXWindowsScreen.cpp,118: window is 0x05200005
DEBUG: CScreen.cpp,38: opened display
DEBUG: CXWindowsScreen.cpp,679: registered hotkey ScrollLock (id=ef14 mask=0000) as id=1
NOTE: synergys.cpp,500: started server
INFO: CServer.cpp,1141: screen "dave-HTPC" shape changed
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
NOTE: CClientListener.cpp,127: accepted client connection
NOTE: CClientProxyUnknown.cpp,279: new client disconnected
^CDEBUG: CXWindowsScreen.cpp,707: unregistered hotkey id=1
DEBUG: CScreen.cpp,49: closed display
NOTE: synergys.cpp,699: stopped server

---

### Post by inmate#001 on 2011-12-02
anyone

---

### Post by CyberCod on 2013-01-16
For the benefit of anyone googling this issue:

I had the same problem, but I couldn't figure out what was wrong until I looked at the command-line output from the other machine.  It was just a matter of having two mismatched versions that wouldn't talk to eachother.

---

