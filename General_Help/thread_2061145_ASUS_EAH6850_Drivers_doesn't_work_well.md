---
title: "ASUS EAH6850 Drivers doesn't work well"
date: 2012-09-21
forum: General Help
---

### Post by kropiyan on 2012-09-21
Hello ubuntu community.

This is my first post and my english is not quite good.

When I installed xubuntu 10.04 Lucid Lynx I couldn't modify the screen resolution

I have a 23' screen, so is 1920x1080.
Video card: ASUS EAH6850
MB: PH67A-C43

So I followed this thread 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
But after the final reboot and write fglrxinfo

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

when I wrote gksudo amdcccle:

> X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 94 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 94 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 66 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    136 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 95 (Unknown request)
  Resource id:  0x17
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    139 (Uknown extension)
  Minor opcode: 95 (Unknown request)
  Resource id:  0x17

It reaches max resolution though, but vertical refresh is extremly slow.

So I implore your help to guide me in the solution of this problem. I don't undertand linux very much. But the concept in fact is very attractive so I want to initiate myself on it, even if my stomach hurt when I see the black and creepy terminal.

Best regards

---

### Post by kropiyan on 2012-09-25
Ok, I finally fixed it:

1. I format HDD
2. Install Xubuntu 10.04 Lucid Lynx
3. I followed this instructions [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) at Manually Installing Catalyst...here I installed QT4 libraries and afterwards I replaced
sudo sh amd-driver-installer-12-6-x86.x86_64.run --buildpkg Ubuntu/oneiric
for
sudo sh amd-driver-installer-12-6-x86.x86_64.run --buildpkg Ubuntu/lucid

after doing
sudo aticonfig --initial
and restart
fglrxinfo
showed me an error. But a messsage from Hardware Drivers said that I have some privative drivers waiting to be activated. So I just activated them and then restart and everything is OK now

---

