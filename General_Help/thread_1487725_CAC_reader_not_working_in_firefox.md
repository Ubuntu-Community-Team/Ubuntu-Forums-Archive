---
title: "CAC reader not working in firefox"
date: 2010-05-19
forum: General Help
---

### Post by uberwulu on 2010-05-19
I am running Ubuntu 9.04 and  need to access goverment sites that require a cac card login.  I followed every instruction posted [http://ohioloco.ubuntuforums.org/showthread.php?t=1221961](http://ohioloco.ubuntuforums.org/showthread.php?t=1221961) on how to set up the cac reader, but it is not working in firefox.  pcsc_scan detects the card reader and the card when it is inserted with the following output:

```

wulu@MLP:~$ pcsc_scan
PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
Scanning present readers
0: O2 Micro Oz776 00 00

Wed May 19 09:38:11 2010
 Reader 0: O2 Micro Oz776 00 00
  Card state: Card removed, 

``````

Wed May 19 09:38:16 2010
 Reader 0: O2 Micro Oz776 00 00
  Card state: Card inserted, 
  ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00

ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00
+ TS = 3B --> Direct Convention
+ T0 = 7D, Y(1): 0111, K: 13 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU (223200 bits/s at 3.57 MHz)
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = 00 --> Extra guard time: 0
+ Historical bytes: 80 31 80 65 B0 83 11 17 D6 83 00 90 00
  Category indicator byte: 80 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: 80
        - Application selection: by full DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 5 (pre-issuing data)
      Data: B0 83 11 17 D6
    Tag: 8, len: 3 (status indicator)
      LCS (life card cycle): 00 (No information given)
      SW: 9000 (Normal processing.)

Possibly identified card (using /home/wulu/.smartcard_list.txt):
3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00
    DoD CAC card issued Jan 14, 2010

```When I loaded the device in firefox's security devices, it loaded fine without any error, but does not allow me to login (the button is disabled).  In the Details pane the status is shown as "not present".  Any suggestions?

---

### Post by PhillB on 2010-06-06
Just tested a friend of mine's CAC card in my Ubuntu setup and it seems that not all CAC cards are created equal. My card is like yours. When running pcsc_scan, the card type that comes up is:

DoD CAC card issued Jan 14, 2010

but my friend's CAC comes up with this

CAC (Common Access Card).

His card detected fine in Firefox and the security device tab was able to pick up his information while mine still said "Not Present". So, I'm thinking about going to the MPF and getting a new CAC card to try. The thing I'll look for is the difference in the chip electrical contacts. The center contact on my card resembles a mastercard logo. It looks like two adjacent circles overlapping in the center. If the new card has that style contact, I'm going to ask for a different one. We'll see happens.

---

### Post by cclukins on 2010-08-23
Mine does exactly the same thing. Did anybody ever get some resolution on this issue?

---

