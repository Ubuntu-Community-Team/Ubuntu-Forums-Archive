---
title: "Anyremote with 5800 - can't connect"
date: 2010-06-09
forum: General Help
---

### Post by themusicalduck on 2010-06-09
I'm trying to setup 10.04 to use anyremote on my Nokia 5800. I've installed all the necessary software, but I can't get gAnyRemote to connect with my phone. Bluetooth works fine otherwise. I can send files to it and set it up as a mobile connection.

On the Device Parameters page I can ping the phone and it works fine, but if I click Test AT I get this error "Can not get port to connect to. Is there any device available?". The phone is listed in the device browser.

If I go to the main window and click Start, it just says Disconnected from phone.

---

### Post by themusicalduck on 2010-06-09
I tried running ganyremote in the terminal, and got this when I clicked Test AT:

```
{'protocol': 'L2CAP', 'name': 'AVRCP Target', 'service-id': None, 'profiles': [('110E', 259)], 'service-classes': ['110C'], 'host': '9C:18:74:92:AB:94', 'provider': 'Symbian Software Ltd.', 'port': 23, 'description': 'Audio Video Remote Control'}
{'protocol': 'RFCOMM', 'name': 'Phonebook access PSE', 'service-id': None, 'profiles': [('1130', 256)], 'service-classes': ['112F'], 'host': '9C:18:74:92:AB:94', 'provider': 'Symbian Software Ltd', 'port': 1, 'description': None}
{'protocol': 'RFCOMM', 'name': 'Hands-Free Audio Gateway', 'service-id': None, 'profiles': [('111E', 261)], 'service-classes': ['111F', '1203'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 2, 'description': None}
{'protocol': 'RFCOMM', 'name': 'Headset Audio Gateway', 'service-id': None, 'profiles': [('1108', 256)], 'service-classes': ['1112', '1203'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 3, 'description': None}
{'protocol': 'L2CAP', 'name': 'Audio Source', 'service-id': None, 'profiles': [('110D', 256)], 'service-classes': ['110A'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 25, 'description': None}
{'protocol': 'L2CAP', 'name': 'AVRCP Controller', 'service-id': None, 'profiles': [('110E', 259)], 'service-classes': ['110E'], 'host': '9C:18:74:92:AB:94', 'provider': 'Symbian Software Ltd.', 'port': 23, 'description': 'Audio Video Remote Control'}
{'protocol': None, 'name': 'PnP Information', 'service-id': None, 'profiles': [], 'service-classes': ['1200'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': None, 'description': None}
{'protocol': 'RFCOMM', 'name': 'SIM Access', 'service-id': None, 'profiles': [('112D', 257)], 'service-classes': ['112D', '1204'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 21, 'description': None}
{'protocol': 'RFCOMM', 'name': None, 'service-id': None, 'profiles': [], 'service-classes': ['00005557-0000-1000-8000-0002EE000001'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 4, 'description': None}
{'protocol': 'RFCOMM', 'name': 'OBEX Object Push', 'service-id': None, 'profiles': [('1105', 256)], 'service-classes': ['1105'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 5, 'description': None}
{'protocol': 'RFCOMM', 'name': 'Imaging', 'service-id': None, 'profiles': [('111A', 256)], 'service-classes': ['111B'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 6, 'description': None}
{'protocol': 'RFCOMM', 'name': 'SyncMLClient', 'service-id': None, 'profiles': [('00000002-0000-1000-8000-0002EE000002', 256)], 'service-classes': ['00000002-0000-1000-8000-0002EE000002'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 7, 'description': None}
{'protocol': 'RFCOMM', 'name': 'OBEX File Transfer', 'service-id': None, 'profiles': [('1106', 256)], 'service-classes': ['1106'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 8, 'description': None}
{'protocol': 'RFCOMM', 'name': 'Nokia OBEX PC Suite Services', 'service-id': None, 'profiles': [('00005005-0000-1000-8000-0002EE000001', 256)], 'service-classes': ['00005005-0000-1000-8000-0002EE000001'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 9, 'description': None}
{'protocol': 'RFCOMM', 'name': 'Nokia SyncML Server', 'service-id': None, 'profiles': [('00005601-0000-1000-8000-0002EE000001', 256)], 'service-classes': ['00005601-0000-1000-8000-0002EE000001'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 10, 'description': None}
{'protocol': 'RFCOMM', 'name': 'Dial-Up Networking', 'service-id': None, 'profiles': [('1103', 256)], 'service-classes': ['1103'], 'host': '9C:18:74:92:AB:94', 'provider': None, 'port': 22, 'description': None}

```

---

### Post by themusicalduck on 2010-06-09
bumpy

---

### Post by ak123 on 2010-06-12
same problem here... im using a nokia E63

---

### Post by kitian on 2010-07-04
I have the same problem with Nokia 5130. I can navigate through the phone and phone card, even I can use my phone as a modem. But, it does not work with anyremote.

---

### Post by kitian on 2010-07-04
It used to work with previous versions of Ubuntu. I am currently running Lucid Lynx.

---

### Post by andytof47 on 2010-09-26
anyone got an answer? 
I'm using e63 as well

fresh install of .debs 

lucid 64bit

0a5c:200a Broadcom Corp. Bluetooth dongle & G

Generic dongle (1131:1004 Integrated System Solution Corp. Bluetooth Device)

anyone please?

---

### Post by andytof47 on 2010-09-26
bump please
:)

it's pretty important and it's difficult to find a thorough howto

so please 


bump:popcorn:

---

### Post by pluxon on 2011-01-14
I don't know if there's someone still interested but here's how I did it through bluetooth.
I've got Ubuntu 64 10.10. My phone is a Nokia 6120 with symbian s60 v3.

1. First I activated bluetooth on the phone and made it visible.

2. Then I went to *System>Preferences>Bluetooth*. I checked the box to make computer visible. Then i continued with *Setup new device*. It detected my phone and asked to input into the phone a pin code dysplayed on the screen (the phone had opened an input field).

3. I installed the *gnayremote* from Ubuntu software center (i have gnome desktop, for KDE there is kanyremote).

4. In ganyremote menu, went *Setup*>*Device browser*. In the new window opened went *File*>*Scan for devices*. Now it should detect the phone and it shoud be displayed as a new entry in the window.
Double click on entry (or in the menu *File>Details*). You could try a ping test pressing the *Ping* button. It should diplay in the status bar "Ping OK !".

5. Upload java client on the phone. My phone has res of 240x320px so I chose the icon set of 48x48. Pressed the "Upload Java" button and my phone promted to accept message from computer.
Message received on phone, I installed the client. Opened the client and went *Options>Enter BT address*.

6. On computer, to find its bluetooth address, I opened a terminal and wrote:
```
hcitool dev
```The output:
```

Devices:
    hci0    00:18:87:03:4B:F8

```7. Copyed the output on the phone without the ":" between the groups and added at the end ":19". The result was: "btspp://001887034BF8:19"

8. On computer, went in ganyremote's original window and selected the application "All-in-1_v2" (it has several useful app) and pressed *Start*.

9. On the phone I selected the address I just wrote, went *Options>Connect* (the computer application must be started first to get this to work). After a few moments the phone screen displayed a list of applications. I was successfull [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

N.B.: I tried the same thing with a nokia 5230 and it worked. Apparently for touchscreen phones it should be uploaded a smaller icon pack (32x32) because the phone emulates the butttons with a dpad on the screen and there isn't enough room for big buttons.

It took me half a day to get is to work but it's worth it!:popcorn:
Good luck!

---

