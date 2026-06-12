---
title: "Nokia E71 + Wammu/Gammu"
date: 2012-04-08
forum: General Help
---

### Post by kamelie1706 on 2012-04-08
Hi,

I try to get my e71 connected via bluetooth.

Software installed:
- Gammu version 1.31.0
- Wammu version 0.35
- python-gammu versino 1.31.0

I have created the gammu config file (~/.gammurc) with only those lines
***
[gammu]
port = BLUETOOTH ADDRESS OF PHONE
connection = blues60
***
as described here
[http://wammu.eu/phones/nokia/5383/](http://wammu.eu/phones/nokia/5383/)

 When I start Wammu I got
Phone connection is not properly configured, can not connect to phone.
(Nothing in the wammu log window)

When using gammu-detect I get
[gammu31]
device = BLUETOOTH ADDRESS OF PHONE
name = E71
connection = bluephonet

=> update my gammu config file
Same results
 
No issue to connect to the phone using dolphin/OBEX

If I start the window wizard/Manual configuration:
I can select my bluetooth device
But when I look in the "connection type" list, I cannot find blues60 module.


When I try automatic detection I get this
Here will appear debug messages from Gammu...
Sun 2012/04/08 18:44:38: [Gammu            - 1.31.0 built 12:52:13 Feb 17 2012 using GCC 4.6]
Sun 2012/04/08 18:44:38: [Connection       - "bluephonet"]
Sun 2012/04/08 18:44:38: [Connection index - 0]
Sun 2012/04/08 18:44:38: [Model type       - ""]
Sun 2012/04/08 18:44:38: [Device           - "BLUETOOTH ADDRESS OF PHONE"]
Sun 2012/04/08 18:44:38: [Running on       - Linux, kernel 3.0.0-17-generic-pae (#30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012)]
Sun 2012/04/08 18:44:38: Looking for suitable channel for PHONET
Sun 2012/04/08 18:44:38: Device BLUETOOTH ADDRESS OF PHONE ("E71")
Sun 2012/04/08 18:44:41:    Channel 1 - "Hands-Free Audio Gateway" (score=0)
Sun 2012/04/08 18:44:41:    Channel 2 - "Headset Audio Gateway" (score=0)
Sun 2012/04/08 18:44:41:    Channel 10 - "SyncMLClient" (score=0)
Sun 2012/04/08 18:44:41:    Channel 11 - "OBEX File Transfer" (score=0)
Sun 2012/04/08 18:44:41:    Channel 12 - "Nokia OBEX PC Suite Services" (score=0)
Sun 2012/04/08 18:44:41:    Channel 13 - "SyncML DM Client" (score=0)
Sun 2012/04/08 18:44:41:    Channel 14 - "Nokia SyncML Server" (score=0)
Sun 2012/04/08 18:44:41:    Channel 3
Sun 2012/04/08 18:44:41:    Channel 9 - "OBEX Object Push" (score=0)
Sun 2012/04/08 18:44:41:    Channel 4 - "Dial-Up Networking" (score=0)
Sun 2012/04/08 18:44:41:    Channel 15 - "Imaging" (score=0)
Sun 2012/04/08 18:44:41: No suitable bluetooth channel found!
Sun 2012/04/08 18:44:41: Init:GSM_TryGetModel failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:41: [Gammu            - 1.31.0 built 12:52:13 Feb 17 2012 using GCC 4.6]
Sun 2012/04/08 18:44:41: [Connection       - "bluefbus"]
Sun 2012/04/08 18:44:41: [Connection index - 0]
Sun 2012/04/08 18:44:41: [Model type       - ""]
Sun 2012/04/08 18:44:41: [Device           - "BLUETOOTH ADDRESS OF PHONE"]
Sun 2012/04/08 18:44:41: [Running on       - Linux, kernel 3.0.0-17-generic-pae (#30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012)]
Sun 2012/04/08 18:44:41: Device BLUETOOTH ADDRESS OF PHONE ("E71")
Sun 2012/04/08 18:44:41:    Channel 1 - "Hands-Free Audio Gateway" (score=0)
Sun 2012/04/08 18:44:41:    Channel 2 - "Headset Audio Gateway" (score=0)
Sun 2012/04/08 18:44:41:    Channel 10 - "SyncMLClient" (score=0)
Sun 2012/04/08 18:44:41:    Channel 11 - "OBEX File Transfer" (score=0)
Sun 2012/04/08 18:44:41:    Channel 12 - "Nokia OBEX PC Suite Services" (score=0)
Sun 2012/04/08 18:44:41:    Channel 13 - "SyncML DM Client" (score=0)
Sun 2012/04/08 18:44:41:    Channel 14 - "Nokia SyncML Server" (score=0)
Sun 2012/04/08 18:44:41:    Channel 3
Sun 2012/04/08 18:44:41:    Channel 9 - "OBEX Object Push" (score=0)
Sun 2012/04/08 18:44:41:    Channel 4 - "Dial-Up Networking" (score=0)
Sun 2012/04/08 18:44:41:    Channel 15 - "Imaging" (score=0)
Sun 2012/04/08 18:44:41: No suitable bluetooth channel found!
Sun 2012/04/08 18:44:41: Init:GSM_TryGetModel failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:41: [Gammu            - 1.31.0 built 12:52:13 Feb 17 2012 using GCC 4.6]
Sun 2012/04/08 18:44:41: [Connection       - "bluerfgnapbus"]
Sun 2012/04/08 18:44:41: [Connection index - 0]
Sun 2012/04/08 18:44:41: [Model type       - ""]
Sun 2012/04/08 18:44:41: [Device           - "BLUETOOTH ADDRESS OF PHONE"]
Sun 2012/04/08 18:44:41: [Running on       - Linux, kernel 3.0.0-17-generic-pae (#30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012)]
Sun 2012/04/08 18:44:41: [Module           - "gnap"]
Sun 2012/04/08 18:44:41: Using hard coded bluetooth channel 14.
Sun 2012/04/08 18:44:41: Connecting to RF channel 14
Sun 2012/04/08 18:44:45: Getting manufacturer
Sun 2012/04/08 18:44:45: SENDING frametype 0x01/length 0x02/2
Sun 2012/04/08 18:44:45: 00 |01                                                          ..              
Sun 2012/04/08 18:44:47: Init:Phone->Initialise failed with error TIMEOUT[14]: No response in specified timeout. Probably phone not connected.
Sun 2012/04/08 18:44:47: Entering GSM_SetIncomingSMS
Sun 2012/04/08 18:44:47: GSM_SetIncomingSMS failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:47: Leaving GSM_SetIncomingSMS
Sun 2012/04/08 18:44:47: Entering GSM_SetIncomingCall
Sun 2012/04/08 18:44:47: GSM_SetIncomingCall failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:47: Leaving GSM_SetIncomingCall
Sun 2012/04/08 18:44:47: Entering GSM_SetIncomingCB
Sun 2012/04/08 18:44:47: GSM_SetIncomingCB failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:47: Leaving GSM_SetIncomingCB
Sun 2012/04/08 18:44:47: Entering GSM_SetIncomingUSSD
Sun 2012/04/08 18:44:47: GSM_SetIncomingUSSD failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:47: Leaving GSM_SetIncomingUSSD
Sun 2012/04/08 18:44:47: [Terminating]
Sun 2012/04/08 18:44:47: [Closing]
Sun 2012/04/08 18:44:47: [Gammu            - 1.31.0 built 12:52:13 Feb 17 2012 using GCC 4.6]
Sun 2012/04/08 18:44:47: [Connection       - "blueat"]
Sun 2012/04/08 18:44:47: [Connection index - 0]
Sun 2012/04/08 18:44:47: [Model type       - ""]
Sun 2012/04/08 18:44:47: [Device           - "BLUETOOTH ADDRESS OF PHONE"]
Sun 2012/04/08 18:44:47: [Running on       - Linux, kernel 3.0.0-17-generic-pae (#30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012)]
Sun 2012/04/08 18:44:47: Looking for suitable channel for AT
Sun 2012/04/08 18:44:47: Device BLUETOOTH ADDRESS OF PHONE ("E71")
Sun 2012/04/08 18:44:47:    Channel 1 - "Hands-Free Audio Gateway" (score=0)
Sun 2012/04/08 18:44:47:    Channel 2 - "Headset Audio Gateway" (score=0)
Sun 2012/04/08 18:44:47:    Channel 10 - "SyncMLClient" (score=0)
Sun 2012/04/08 18:44:47:    Channel 11 - "OBEX File Transfer" (score=0)
Sun 2012/04/08 18:44:47:    Channel 12 - "Nokia OBEX PC Suite Services" (score=0)
Sun 2012/04/08 18:44:47:    Channel 13 - "SyncML DM Client" (score=0)
Sun 2012/04/08 18:44:47:    Channel 14 - "Nokia SyncML Server" (score=0)
Sun 2012/04/08 18:44:47:    Channel 3
Sun 2012/04/08 18:44:47:    Channel 9 - "OBEX Object Push" (score=0)
Sun 2012/04/08 18:44:47:    Channel 4 - "Dial-Up Networking" (score=0)
Sun 2012/04/08 18:44:47:    Channel 15 - "Imaging" (score=0)
Sun 2012/04/08 18:44:47: No suitable bluetooth channel found!
Sun 2012/04/08 18:44:47: Init:GSM_TryGetModel failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:47: [Gammu            - 1.31.0 built 12:52:13 Feb 17 2012 using GCC 4.6]
Sun 2012/04/08 18:44:47: [Connection       - "blueobex"]
Sun 2012/04/08 18:44:47: [Connection index - 0]
Sun 2012/04/08 18:44:47: [Model type       - ""]
Sun 2012/04/08 18:44:47: [Device           - "BLUETOOTH ADDRESS OF PHONE"]
Sun 2012/04/08 18:44:47: [Running on       - Linux, kernel 3.0.0-17-generic-pae (#30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012)]
Sun 2012/04/08 18:44:47: [Module           - "obex|seobex|obexfs|obexirmc|obexnone|mobex"]
Sun 2012/04/08 18:44:47: Looking for suitable channel for OBEX
Sun 2012/04/08 18:44:47: Device BLUETOOTH ADDRESS OF PHONE ("E71")
Sun 2012/04/08 18:44:47:    Channel 1 - "Hands-Free Audio Gateway" (score=0)
Sun 2012/04/08 18:44:47:    Channel 2 - "Headset Audio Gateway" (score=0)
Sun 2012/04/08 18:44:47:    Channel 10 - "SyncMLClient" (score=0)
Sun 2012/04/08 18:44:47:    Channel 11 - "OBEX File Transfer" (score=3)
Sun 2012/04/08 18:44:47:    Channel 12 - "Nokia OBEX PC Suite Services" (score=3)
Sun 2012/04/08 18:44:47:    Channel 13 - "SyncML DM Client" (score=0)
Sun 2012/04/08 18:44:47:    Channel 14 - "Nokia SyncML Server" (score=0)
Sun 2012/04/08 18:44:47:    Channel 3
Sun 2012/04/08 18:44:47:    Channel 9 - "OBEX Object Push" (score=2)
Sun 2012/04/08 18:44:47:    Channel 4 - "Dial-Up Networking" (score=0)
Sun 2012/04/08 18:44:47:    Channel 15 - "Imaging" (score=0)
Sun 2012/04/08 18:44:47: Connecting to RF channel 11
Sun 2012/04/08 18:44:50: Connected using model 
Sun 2012/04/08 18:44:50: Folder Browsing service requested
Sun 2012/04/08 18:44:50: Connecting
Sun 2012/04/08 18:44:50: SENDING frametype 0x80/length 0x17/23
Sun 2012/04/08 18:44:50: 10 |00 |04 |00 |46F|00 |13 |F9 |EC |7B{|C4 |95 |3C<|11 |D2 |98  ....F....{..<...
Sun 2012/04/08 18:44:50: 4EN|52R|54T|00 |DC |9E |09                                      NRT....         
Sun 2012/04/08 18:44:50: RECEIVED frametype 0xA0/length 0x1C/28
Sun 2012/04/08 18:44:50: 10 |00 |40@|00 |CB |C3 |0F |A5 |96 |4AJ|00 |13 |F9 |EC |7B{|C4  ..@......J....{.
Sun 2012/04/08 18:44:50: 95 |3C<|11 |D2 |98 |4EN|52R|54T|00 |DC |9E |09                  .<...NRT....    
Sun 2012/04/08 18:44:50: Connected/disconnected OK
Sun 2012/04/08 18:44:50: Maximal size of frame is 16384 0x4000
Sun 2012/04/08 18:44:50: No filename requested, grabbing OBEX capabilities as obex-capability.xml
Sun 2012/04/08 18:44:50: Getting first file part
Sun 2012/04/08 18:44:50: SENDING frametype 0x83/length 0x19/25
Sun 2012/04/08 18:44:50: CB |C3 |0F |A5 |96 |42B|00 |14 |78x|2D-|6Fo|62b|65e|78x|2F/|63c .....B..x-obex/c
Sun 2012/04/08 18:44:50: 61a|70p|61a|62b|69i|6Cl|69i|74t|79y                             apability       
Sun 2012/04/08 18:44:50: RECEIVED frametype 0xC3/length 0x00/0
Sun 2012/04/08 18:44:50: Security error (0xc3)
Sun 2012/04/08 18:44:50: Retry 1
Sun 2012/04/08 18:44:50: SENDING frametype 0x83/length 0x19/25
Sun 2012/04/08 18:44:50: CB |C3 |0F |A5 |96 |42B|00 |14 |78x|2D-|6Fo|62b|65e|78x|2F/|63c .....B..x-obex/c
Sun 2012/04/08 18:44:50: 61a|70p|61a|62b|69i|6Cl|69i|74t|79y                             apability       
Sun 2012/04/08 18:44:50: RECEIVED frametype 0xC3/length 0x00/0
Sun 2012/04/08 18:44:50: Security error (0xc3)
Sun 2012/04/08 18:44:50: Retry 2
Sun 2012/04/08 18:44:50: SENDING frametype 0x83/length 0x19/25
Sun 2012/04/08 18:44:50: CB |C3 |0F |A5 |96 |42B|00 |14 |78x|2D-|6Fo|62b|65e|78x|2F/|63c .....B..x-obex/c
Sun 2012/04/08 18:44:50: 61a|70p|61a|62b|69i|6Cl|69i|74t|79y                             apability       
Sun 2012/04/08 18:44:51: RECEIVED frametype 0xC3/length 0x00/0
Sun 2012/04/08 18:44:51: Security error (0xc3)
Sun 2012/04/08 18:44:51: Retry 3
Sun 2012/04/08 18:44:51: SENDING frametype 0x83/length 0x19/25
Sun 2012/04/08 18:44:51: CB |C3 |0F |A5 |96 |42B|00 |14 |78x|2D-|6Fo|62b|65e|78x|2F/|63c .....B..x-obex/c
Sun 2012/04/08 18:44:51: 61a|70p|61a|62b|69i|6Cl|69i|74t|79y                             apability       
Sun 2012/04/08 18:44:51: RECEIVED frametype 0xC3/length 0x00/0
Sun 2012/04/08 18:44:51: Security error (0xc3)
Sun 2012/04/08 18:44:51: Retry 4
Sun 2012/04/08 18:44:51: SENDING frametype 0x83/length 0x19/25
Sun 2012/04/08 18:44:51: CB |C3 |0F |A5 |96 |42B|00 |14 |78x|2D-|6Fo|62b|65e|78x|2F/|63c .....B..x-obex/c
Sun 2012/04/08 18:44:51: 61a|70p|61a|62b|69i|6Cl|69i|74t|79y                             apability       
Sun 2012/04/08 18:44:51: RECEIVED frametype 0xC3/length 0x00/0
Sun 2012/04/08 18:44:51: Security error (0xc3)
Sun 2012/04/08 18:44:51: Disconnecting
Sun 2012/04/08 18:44:51: SENDING frametype 0x81/length 0x00/0
Sun 2012/04/08 18:44:51: RECEIVED frametype 0xD3/length 0x00/0
Sun 2012/04/08 18:44:51: Internal phone error (0xd3)
Sun 2012/04/08 18:44:51: [Connected]
Sun 2012/04/08 18:44:51: Entering GSM_GetModel
Sun 2012/04/08 18:44:51: GSM_GetModel failed with error NOTSUPPORTED[21]: Function not supported by phone.
Sun 2012/04/08 18:44:51: Leaving GSM_GetModel
Sun 2012/04/08 18:44:51: Entering GSM_SetIncomingSMS
Sun 2012/04/08 18:44:51: GSM_SetIncomingSMS failed with error NOTIMPLEMENTED[25]: Functionality not implemented. You are welcome to help authors with it.
Sun 2012/04/08 18:44:51: Leaving GSM_SetIncomingSMS
Sun 2012/04/08 18:44:51: Entering GSM_SetIncomingCall
Sun 2012/04/08 18:44:51: GSM_SetIncomingCall failed with error NOTIMPLEMENTED[25]: Functionality not implemented. You are welcome to help authors with it.
Sun 2012/04/08 18:44:51: Leaving GSM_SetIncomingCall
Sun 2012/04/08 18:44:51: Entering GSM_SetIncomingCB
Sun 2012/04/08 18:44:51: GSM_SetIncomingCB failed with error NOTIMPLEMENTED[25]: Functionality not implemented. You are welcome to help authors with it.
Sun 2012/04/08 18:44:51: Leaving GSM_SetIncomingCB
Sun 2012/04/08 18:44:51: Entering GSM_SetIncomingUSSD
Sun 2012/04/08 18:44:51: GSM_SetIncomingUSSD failed with error NOTIMPLEMENTED[25]: Functionality not implemented. You are welcome to help authors with it.
Sun 2012/04/08 18:44:51: Leaving GSM_SetIncomingUSSD
Sun 2012/04/08 18:44:51: [Terminating]
Sun 2012/04/08 18:44:51: Disconnecting
Sun 2012/04/08 18:44:51: SENDING frametype 0x81/length 0x00/0
Sun 2012/04/08 18:44:51: RECEIVED frametype 0xD3/length 0x00/0
Sun 2012/04/08 18:44:51: Internal phone error (0xd3)

Am I missing something?

---

### Post by kamelie1706 on 2012-04-15
anyone or so obvious that I do not find the good how-to/tutorial?

---

