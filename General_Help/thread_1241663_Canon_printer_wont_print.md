---
title: "Canon printer wont print"
date: 2009-08-16
forum: General Help
---

### Post by tropdoug on 2009-08-16
I am having an issue getting a conon LBP3200 working on my 8.10 OS. 

I have followed the step by step here [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

substituting my model obviously, but when I run the test command of 

> douglas@desktop:~$ **sudo ccpdadmin**

Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP3200     : usb         : //Canon/LBP3200     : /dev/usblp0     :
The backen is listed as **usb** but the installation instructions tell me it should be **ccp**

When I do the  next test 

> douglas@desktop:~$ captstatusui -P LBP3200
*** captstatusui Socket Error ***I get the socket error. 

The printer shows in the admin printers and as you can see (image attached) its apparently on line, but both the queued jobs just sit there. 

Any help gratefully accepted.

---

### Post by tropdoug on 2009-08-17
Bump

---

