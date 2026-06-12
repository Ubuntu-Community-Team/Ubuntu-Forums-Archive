---
title: "Strange gnokii problems"
date: 2010-09-28
forum: General Help
---

### Post by E_K on 2010-09-28
ok so i got gnokii setup and working, all was working perfectly.
I have several computers sending a sms.sh file through putty to the server, in the file is the command to send an sms

```

echo "my message" | gnokii --sendsms 0654321234

```

well i lost power at home and my server turned off, so i rebooted. Made the huawei E1750 do its flipflop thing to make it seen as a modem not a storage device.
/dev/ttyUSB0 permissions 777

Now its will rarely send an sms, sometimes it will but most of the time it just errors out below is the output. I am now sending the command logged in to the server through a ssh shell, to rule out a problem of sending the script.

I have tried forcing the smsc, same error... I'm kinda out of ideas. What bothers me it was working so well before power loss.

I have also reinstalled gnokii, and also downloaded the newest version from source and built --- same error.

Well heres the output:

```

GNOKII Version 0.6.12
LOG: debug mask is 0x1
phone instance config:
model: AT-HW
port_device: /dev/ttyUSB0
connection_type: 0
init_length: 0
serial_baudrate: 9600
serial_write_usleep: -1
hardware_handshake: 1
require_dcd: 0
smsc_timeout: 300
connect_script:
disconnect_script:
rfcomm_cn: 1
sm_retry: off
Initializing AT capable mobile phone ...
Serial device: opening device /dev/ttyUSB0
Serial device: setting RTS to high and DTR to high
Serial device: setting RTS to high and DTR to low
Serial device: setting RTS to high and DTR to high
Message sent: 0x00 / 0x0004
41 54 5a 0d                                     | ATZ
write: [ATZ<cr>]
read : [ATZ<cr><cr><lf>OK<cr><lf>]
Message received: 0x00 / 0x000a
02 41 54 5a 0d 0d 0a 4f 4b 0d                   |  ATZ   OK
Received message type 00
Message sent: 0x00 / 0x0005
41 54 45 31 0d                                  | ATE1
write: [ATE1<cr>]
read : [ATE1<cr><cr><lf>OK<cr><lf>]
Message received: 0x00 / 0x000b
02 41 54 45 31 0d 0d 0a 4f 4b 0d                |  ATE1   OK
Received message type 00
Message sent: 0x00 / 0x000a
41 54 2b 43 4d 45 45 3d 31 0d                   | AT+CMEE=1
write: [AT+CMEE=1<cr>]
read : [AT+CMEE=1<cr><cr><lf>OK<cr><lf>]
Message received: 0x00 / 0x0010
02 41 54 2b 43 4d 45 45 3d 31 0d 0d 0a 4f 4b 0d |  AT+CMEE=1   OK
Received message type 00
Message sent: 0x06 / 0x0008
41 54 2b 43 47 4d 4d 0d                         | AT+CGMM
write: [AT+CGMM<cr>]
read : [AT+CGMM<cr><cr><lf>E1750<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x06 / 0x0017
02 41 54 2b 43 47 4d 4d 0d 0d 0a 45 31 37 35 30 |  AT+CGMM   E1750
0d 0a 0d 0a 4f 4b 0d                            |     OK
Received message type 06
Message sent: 0x06 / 0x0008
41 54 2b 43 47 4d 49 0d                         | AT+CGMI
write: [AT+CGMI<cr>]
read : [AT+CGMI<cr><cr><lf>huawei<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x06 / 0x0018
02 41 54 2b 43 47 4d 49 0d 0d 0a 68 75 61 77 65 |  AT+CGMI   huawe
69 0d 0a 0d 0a 4f 4b 0d                         | i    OK
Received message type 06
Message sent: 0x61 / 0x0009
41 54 2b 43 53 43 53 3f 0d                      | AT+CSCS?
write: [AT+CSCS?<cr>]
read : [AT+CSCS?<cr><cr><lf>+CSCS: "IRA"<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x61 / 0x001f
02 41 54 2b 43 53 43 53 3f 0d 0d 0a 2b 43 53 43 |  AT+CSCS?   +CSC
53 3a 20 22 49 52 41 22 0d 0a 0d 0a 4f 4b 0d    | S: "IRA"    OK
Received message type 61
Initialisation completed
Message sent: 0x23 / 0x0009
41 54 2b 43 53 43 41 3f 0d                      | AT+CSCA?
write: [AT+CSCA?<cr>]
read : [AT+CSCA?<cr><cr><lf>+CSCA: "+316540881000",145<cr><lf><cr><lf>OK<cr><lf>                                                                                                 ]
Message received: 0x23 / 0x002d
02 41 54 2b 43 53 43 41 3f 0d 0d 0a 2b 43 53 43 |  AT+CSCA?   +CSC
41 3a 20 22 2b 33 31 36 35 34 30 38 38 31 30 30 | A: "+31654088100
30 22 2c 31 34 35 0d 0a 0d 0a 4f 4b 0d          | 0",145    OK
Received message type 23
General Data Coding
dcs: 0x0
Length: 0x69
user_data_length: 0x5c
ValidityIndicator: 2
user_data: C432684E0FD3EB73903DEC06D5EF2079191E9687E9E932283D079DCB7538394C2FB34                                                                                                 075D0BAEEA683C8693A68FC76D3E56F76595E7683DE70D0FD7E7791CBE779DB1C76BBDC6C90B4190                                                                                                 4B9EBED7659AE93D16232582D7693C16230
Sending
Message sent: 0x63 / 0x000a
41 54 2b 43 4d 47 46 3d 30 0d                   | AT+CMGF=0
write: [AT+CMGF=0<cr>]
read : [AT+CMGF=0<cr><cr><lf>OK<cr><lf>]
Message received: 0x63 / 0x0010
02 41 54 2b 43 4d 47 46 3d 30 0d 0d 0a 4f 4b 0d |  AT+CMGF=0   OK
Received message type 63
PDU mode set
Sending initial sequence
Message sent: 0x64 / 0x000c
41 54 2b 43 4d 47 53 3d 31 30 35 0d             | AT+CMGS=105
write: [AT+CMGS=105<cr>]
read : [AT+CMGS=105<cr><cr><lf>> ]
Message received: 0x64 / 0x0010
01 41 54 2b 43 4d 47 53 3d 31 30 35 0d 0d 0a 3e |  AT+CMGS=105   >
Received message type 64
Got response 0
Sending frame: 079113560488010011000A8160022929540000AA69C432684E0FD3EB73903DEC0                                                                                                 6D5EF2079191E9687E9E932283D079DCB7538394C2FB34075D0BAEEA683C8693A68FC76D3E56F765                                                                                                 95E7683DE70D0FD7E7791CBE779DB1C76BBDC6C90B41904B9EBED7659AE93D16232582D7693C1623                                                                                                 0
Message sent: 0x21 / 0x00e3
30 37 39 31 31 33 35 36 30 34 38 38 30 31 30 30 | 0791135604880100
31 31 30 30 30 41 38 31 36 30 30 32 32 39 32 39 | 11000A8160022929
35 34 30 30 30 30 41 41 36 39 43 34 33 32 36 38 | 540000AA69C43268
34 45 30 46 44 33 45 42 37 33 39 30 33 44 45 43 | 4E0FD3EB73903DEC
30 36 44 35 45 46 32 30 37 39 31 39 31 45 39 36 | 06D5EF2079191E96
38 37 45 39 45 39 33 32 32 38 33 44 30 37 39 44 | 87E9E932283D079D
43 42 37 35 33 38 33 39 34 43 32 46 42 33 34 30 | CB7538394C2FB340
37 35 44 30 42 41 45 45 41 36 38 33 43 38 36 39 | 75D0BAEEA683C869
33 41 36 38 46 43 37 36 44 33 45 35 36 46 37 36 | 3A68FC76D3E56F76
35 39 35 45 37 36 38 33 44 45 37 30 44 30 46 44 | 595E7683DE70D0FD
37 45 37 37 39 31 43 42 45 37 37 39 44 42 31 43 | 7E7791CBE779DB1C
37 36 42 42 44 43 36 43 39 30 42 34 31 39 30 34 | 76BBDC6C90B41904
42 39 45 42 45 44 37 36 35 39 41 45 39 33 44 31 | B9EBED7659AE93D1
36 32 33 32 35 38 32 44 37 36 39 33 43 31 36 32 | 6232582D7693C162
33 30 1a                                        | 30
write: [079113560488010011000A8160022929540000AA69C432684E0FD3EB73903DEC06D5EF20                                                                                                 79191E9687E9E932283D079DCB7538394C2FB34075D0BAEEA683C8693A68FC76D3E56F76595E7683                                                                                                 DE70D0FD7E7791CBE779DB1C76BBDC6C90B41904B9EBED7659AE93D16232582D7693C16230^Z]
Serial write: transmitter busy, waiting
Serial write: transmitter ready
read : [^A^49113560488010011000A8160022929540000AA69C432684E0FD3EB73903DEC06D5EF                                                                                                 2079191E9687E9E932283D079DCB7538394C2FB34075D0BAEEA683C869<cr><lf><cr><lf>+CMS E                                                                                                 RROR: 500<cr><lf>]
Message received: 0x21 / 0x0095
04 01 f4 39 31 31 33 35 36 30 34 38 38 30 31 30 |    9113560488010
30 31 31 30 30 30 41 38 31 36 30 30 32 32 39 32 | 011000A816002292
39 35 34 30 30 30 30 41 41 36 39 43 34 33 32 36 | 9540000AA69C4326
38 34 45 30 46 44 33 45 42 37 33 39 30 33 44 45 | 84E0FD3EB73903DE
43 30 36 44 35 45 46 32 30 37 39 31 39 31 45 39 | C06D5EF2079191E9
36 38 37 45 39 45 39 33 32 32 38 33 44 30 37 39 | 687E9E932283D079
44 43 42 37 35 33 38 33 39 34 43 32 46 42 33 34 | DCB7538394C2FB34
30 37 35 44 30 42 41 45 45 41 36 38 33 43 38 36 | 075D0BAEEA683C86
39 0d 0a 0d 0a 2b 43 4d 53 20 45 52 52 4f 52 3a | 9    +CMS ERROR:
20 35 30 30 0d                                  |  500
Received message type 21
SMS Send failed (Unknown error - well better than nothing!!)
Serial device: closing device


```

---

### Post by E_K on 2010-09-29
well out of the blue it started working again :S Suppose its time to play the waiting game...

---

### Post by E_K on 2011-03-07
and now its doing the same thing :S

no-one any ideas :( ?!?

---

### Post by E_K on 2011-03-12
bump?

---

### Post by amolshastry on 2012-05-02
The problem for me with modem was due to network. i had to reboot the modem to get it working.

---

### Post by Alan Baldwin on 2013-03-04
SCRUMstudy is offering Scrum and Agile training and certifications. These courses are approved by PMI for PDUs. They also offer Risk Management course for free with these courses. To know more about these courses and the advantages, visit: [http://www.scrumstudy.com/index.asp](http://www.scrumstudy.com/index.asp)

---

