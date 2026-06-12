---
title: "working lucent Agere Systems 56k WinModem"
date: 2009-10-08
forum: General Help
---

### Post by sdowney717 on 2009-10-08
first run scanmodem

> scott2@scott2-desktop:~/scanmodem$ sudo ./scanModem
UPDATE=2009_09_15
 Continuing as this update is only 3 weeks old,
 but the current Update is always at: [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)


Identifying PCI bus slots with candidate modems.
Running PCIbus cases
Analysing card in PCI bus 05:09.0, writing to scanout.05:09.0
Using scanout.05:09.0 data, and writing guidance to ModemData.txt
Writing DOCs/AgereDSP.txt

 Writing residual guidance customized to your System.
   A subfolder Modem/  has been written,  containing these files with more detailed Information: 
 ------------------------------------------------------------------------------------------
 1stRead.txt  Bootup.txt  dmesg.txt  DOCs  ModemData.txt  scanout.05:09.0  tmp
    and in the DOCs subfolder:
 AgereDSP.txt  DriverCompiling.txt  InfoGeneral.txt  LSI_Agere.txt
Rational.txt  SoftModem.txt	   Testing.txt	    UNSUBSCRIBE.txt
wvdial.txt    YourSystem.txt
-------------------------------------------------------------------------------------------
       Please read 1stRead.txt first for Guidance.



this file ModemData.txt found in the modem subdirectory of scanmodem, will tell you what to do, in my case the file is here

[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) get the martian-full-20080625.tar.gz

unpack it and go into the directory
type "make"
type "sudo make install"

run these 2 commands
scott2@scott2-desktop:~/martian-full-20080625$ sudo modprobe martian_dev

scott2@scott2-desktop:~/martian-full-20080625$ sudo martian_modem
martian: info: Your port is /dev/ttySM0

then you can setup wvdial to prove it exists at /dev/ttySM0
you will have to run martian-modem at every boot to run the program.

> scott2@scott2-desktop:~/scanmodem$ sudo wvdialconf
[sudo] password for scott2: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySM0<*1>: ATQ0 V1 E1 -- OK
ttySM0<*1>: ATQ0 V1 E1 Z -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.30
ttySM0<*1>: Speed 4800: AT -- OK
ttySM0<*1>: Speed 9600: AT -- OK
ttySM0<*1>: Speed 19200: AT -- OK
ttySM0<*1>: Speed 38400: AT -- OK
ttySM0<*1>: Speed 57600: AT -- OK
ttySM0<*1>: Speed 115200: AT -- OK
ttySM0<*1>: Speed 230400: AT -- OK
ttySM0<*1>: Speed 460800: AT -- OK
ttySM0<*1>: Max speed is 460800; that should be safe.
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttySM0.
Modem configuration written to /etc/wvdial.conf.
ttySM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
scott2@scott2-desktop:~/scanmodem$ 


additional information is here
[http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)

I did this in Karmic-Koala

---

### Post by mustangzach on 2009-10-09
Great tutorial here, however, you should mention for newbies that you also need the build-essential (and makedev?) package for compiling this.

But this will come in handy soon, as I have a few lucent modems lying around and my grandparents still have dial up.

---

