---
title: "Ventrilo"
date: 2010-06-05
forum: General Help
---

### Post by Dan_Solo on 2010-06-05
Hello. I am new to ubuntu and I would like host a ventrilo server. I followed all the instructions and I get to the part where you type ./ventrilo_srv and I get this:

./ventrilo/ventrilo_srv
Ventrilo Server - Public - Version 3.0.3
(c)Copyright 1999-2008 Flagship Industries, Inc.

Unable to open configuration file 'ventrilo_srv.ini'.
ERROR: Unable to read configuration data. Exiting.
aragorn@PolyphiricHemophelia:~$ cd ventrilo
aragorn@PolyphiricHemophelia:~/ventrilo$ ./ventrilo_srv
Ventrilo Server - Public - Version 3.0.3
(c)Copyright 1999-2008 Flagship Industries, Inc.

Version           = 3.0.3
Name              = WW3
Phonetic          = Server 1
Auth              = 0
Duplicates        = 1
SendBuffer        = 131072
RecvBuffer        = 131072
LogonTimeout      = 5
CloseStd          = 1
TimeStamp         = 0
PingRate          = 10
ExtraBuffer       = 131072
ChanWidth         = 0
ChanDepth         = 8
ChanClients       = 0
DisableQuit       = 0
VoiceCodec        = 0 (GSM 6.10)
VoiceFormat       = 1 (11 KHz, 16 bit) - Bytes/Sec 2210
SilentLobby       = 0
AutoKick          = 0
MaxClients        = 8


ERROR: Unable to bind to TCP socket.

I don't know what causes the the unable to bind to TCP socket.

---

### Post by Dan_Solo on 2010-06-05
I'm trying to get a server ventrilo. I followed theire instructions until when i am promted to enter ./ventrilo_srv.

~/ventrilo$ ./ventrilo_srv
Ventrilo Server - Public - Version 3.0.3
(c)Copyright 1999-2008 Flagship Industries, Inc.

Version           = 3.0.3
Name              = WW3
Phonetic          = Server 1
Auth              = 0
Duplicates        = 1
SendBuffer        = 131072
RecvBuffer        = 131072
LogonTimeout      = 5
CloseStd          = 1
TimeStamp         = 0
PingRate          = 10
ExtraBuffer       = 131072
ChanWidth         = 0
ChanDepth         = 8
ChanClients       = 0
DisableQuit       = 0
VoiceCodec        = 0 (GSM 6.10)
VoiceFormat       = 1 (11 KHz, 16 bit) - Bytes/Sec 2210
SilentLobby       = 0
AutoKick          = 0
MaxClients        = 8


ERROR: Unable to bind to TCP socket.

What can I do to make this work and allow it to bind to tcp socket?

---

### Post by cariboo on 2010-06-05
Please don't create multiple threads on the same subject, I have merged your two threads.

---

