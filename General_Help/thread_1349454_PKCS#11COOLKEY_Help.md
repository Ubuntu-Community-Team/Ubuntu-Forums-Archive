---
title: "PKCS#11/COOLKEY Help"
date: 2009-12-08
forum: General Help
---

### Post by marcello.mezzanotti on 2009-12-08
Im using Ubuntu 9.10 (LinuxMint) and trying to configure pam_pkcs11, as you can see bellow my card reader and smartcard are recognized:


user@linuxmint ~ $ pcsc_scan
PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
Scanning present readers...
0: SCM SCR 3310 (21120514101143) 00 00

Tue Dec  8 12:15:16 2009
 Reader 0: SCM SCR 3310 (21120514101143) 00 00
  Card state: Card inserted,
  ATR: 3B B7 94 00 81 31 FE 65 53 50 4B 32 33 90 00 D1

ATR: 3B B7 94 00 81 31 FE 65 53 50 4B 32 33 90 00 D1
+ TS = 3B --> Direct Convention
+ T0 = B7, Y(1): 1011, K: 7 (historical bytes)
  TA(1) = 94 --> Fi=512, Di=8, 64 cycles/ETU
    62500 bits/s at 4 MHz, fMax for Fi = 5 MHz => 78125 bits/s
  TB(1) = 00 --> VPP is not electrically connected
  TD(1) = 81 --> Y(i+1) = 1000, Protocol T = 1
-----
  TD(2) = 31 --> Y(i+1) = 0011, Protocol T = 1
-----
  TA(3) = FE --> IFSC: 254
  TB(3) = 65 --> Block Waiting Integer: 6 - Character Waiting Integer: 5
+ Historical bytes: 53 50 4B 32 33 90 00
  Category indicator byte: 53 (proprietary format)
+ TCK = D1 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B B7 94 00 81 31 FE 65 53 50 4B 32 33 90 00 D1
        Giesecke & Devrient Starcos 2.3
        Deutsche Bank WebSign (RSA-Card)
        G&D StarSign Token



my coolkey part of pam_pkcs11.config 

  # coolkey
  pkcs11_module coolkey {
    module = /usr/lib/pkcs11/libcoolkeypk11.so;
    description = "Cool Key";
    slot_num = 0;
    support_threads = true;
    ca_dir = /etc/pam_pkcs11/cacerts;
    crl_dir = /etc/pam_pkcs11/crls;
    cert_policy = none;
  }

if i try pklogin_finder i got this:

linuxmint ~ # pklogin_finder debug
DEBUG am_config.c:208: Using config file /etc/pam_pkcs11/pam_pkcs11.conf
DEBUG am_config.c:298: argument pklogin_finder is not supported by this module
DEBUG klogin_finder.c:66: loading pkcs #11 module...
DEBUG kcs11_lib.c:742: PKCS #11 module = [/usr/lib/pkcs11/libcoolkeypk11.so]
DEBUG kcs11_lib.c:759: module permissions: uid = 0, gid = 0, mode = 644
DEBUG kcs11_lib.c:768: loading module /usr/lib/pkcs11/libcoolkeypk11.so
DEBUG kcs11_lib.c:776: getting function list
DEBUG klogin_finder.c:74: initialising pkcs #11 module...
DEBUG klogin_finder.c:78: init_pkcs11_module() failed: C_Initialize() failed: a


any guess/help?

thank you,
marcello

---

