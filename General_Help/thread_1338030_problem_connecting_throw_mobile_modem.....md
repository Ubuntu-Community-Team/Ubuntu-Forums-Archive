---
title: "problem connecting throw mobile modem...."
date: 2009-11-26
forum: General Help
---

### Post by muctadir on 2009-11-26
i am using kubuntu 9.10 64 bit. i need to use internet using a mobile modem. my mobiles modem is MT6225. when i connect my mobile kubuntu recognises my mobile modem.

output for lsusb is-

Bus 002 Device 003: ID 0e8d:0003 MediaTek Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


when i click on network manager to connect, it tries to connect for a few seconds and then it fails to connect. i used wvdial to connect. this is what happens to wvdial-


dinar@pc-dinar:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM6: No such file or directory
--> Cannot open /dev/ttyACM6: No such file or directory
--> Cannot open /dev/ttyACM6: No such file or directory
dinar@pc-dinar:~$ sudo wvdial                          
[sudo] password for dinar:                             
--> WvDial: Internet dialer version 1.60               
--> Cannot open /dev/ttyACM6: No such file or directory
--> Cannot open /dev/ttyACM6: No such file or directory
--> Cannot open /dev/ttyACM6: No such file or directory
dinar@pc-dinar:~$ sudo wvdialconf                 
Editing `/etc/wvdial.conf'.                       

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.        
Modem Port Scan<*1>: S1   S2   S3                                    
ttyACM0<Info>: Device or resource busy                               
Modem Port Scan<*1>: ACM0                                            
WvModem<*1>: Cannot get information for serial port.                 
ttyACM1<*1>: ATQ0 V1 E1 -- OK                                        
ttyACM1<*1>: ATQ0 V1 E1 Z -- OK                                      
ttyACM1<*1>: ATQ0 V1 E1 S0=0 -- OK                                   
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK                               
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK                           
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK                 
ttyACM1<*1>: Modem Identifier: ATI -- MTK2                           
ttyACM1<*1>: Speed 4800: AT -- OK                                    
ttyACM1<*1>: Speed 9600: AT -- OK                                    
ttyACM1<*1>: Speed 19200: AT -- OK                                   
ttyACM1<*1>: Speed 38400: AT -- OK                                   
ttyACM1<*1>: Speed 57600: AT -- OK                                   
ttyACM1<*1>: Speed 115200: AT -- OK                                  
ttyACM1<*1>: Speed 230400: AT -- OK                                  
ttyACM1<*1>: Speed 460800: AT -- OK                                  
ttyACM1<*1>: Max speed is 460800; that should be safe.               
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK                 

Found an USB modem on /dev/ttyACM1.
Modem configuration written to /etc/wvdial.conf.
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
dinar@pc-dinar:~$ sudo kate /etc/wvdial.conf
Error: "/var/tmp/kdecache-dinar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dinar" is owned by uid 1000 instead of uid 0.         
Error: "/tmp/kde-dinar" is owned by uid 1000 instead of uid 0.         
Error: "/tmp/ksocket-dinar" is owned by uid 1000 instead of uid 0.     
kdeinit4: Shutting down running client.                                
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so        
Error: "/tmp/ksocket-dinar" is owned by uid 1000 instead of uid 0.     
Error: "/tmp/kde-dinar" is owned by uid 1000 instead of uid 0.         
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so            
Error: "/var/tmp/kdecache-dinar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dinar" is owned by uid 1000 instead of uid 0.         
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so    
kbuildsycoca4 running...                                               
Error: "/var/tmp/kdecache-dinar" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so    
kbuildsycoca4 running...                                               
Error: "/var/tmp/kdecache-dinar" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-dinar" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so     
Error: "/tmp/ksocket-dinar" is owned by uid 1000 instead of uid 0.     
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so                
QThreadStorage: Thread 0x1b761c0 exited after QThreadStorage 2147483636 destroyed
dinar@pc-dinar:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.                    
--> Sending: ATZ                           
ATZ                                        
OK                                         
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0             
OK                                            
--> Modem initialized.                        
--> Sending: ATZ*99***1#                      
--> Waiting for carrier.                      
ATZ*99***1#                                   
OK                                            
--> Timed out while dialing.  Trying again.   
--> Sending: ATZ*99***1#                      
--> Waiting for carrier.                      
ATZ*99***1#                                   
OK                                            
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Thu Nov 26 13:59:17 2009       
dinar@pc-dinar:~$ sudo kate /etc/wvdial.conf        
Error: "/var/tmp/kdecache-dinar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-dinar" is owned by uid 1000 instead of uid 0.         
Error: "/tmp/ksocket-dinar" is owned by uid 1000 instead of uid 0.     
QThreadStorage: Thread 0x10a51c0 exited after QThreadStorage 2147483636 destroyed
dinar@pc-dinar:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.                    
--> Sending: ATZ                           
ATZ                                        
OK                                         
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0             
OK                                            
--> Modem initialized.                        
--> Sending: ATZ*99#                          
--> Waiting for carrier.                      
ATZ*99#                                       
OK                                            
--> Timed out while dialing.  Trying again.
--> Sending: ATZ*99#
--> Waiting for carrier.
ATZ*99#
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATZ*99#
--> Waiting for carrier.
ATZ*99#
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATZ*99#
--> Waiting for carrier.
ATZ*99#
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATZ*99#
--> Waiting for carrier.
ATZ*99#
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATZ*99#
--> Waiting for carrier.
ATZ*99#
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATZ*99#
--> Waiting for carrier.
ATZ*99#
OK
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Thu Nov 26 14:05:33 2009


wvdial.conf is here-


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyACM1
Username = 1
Dial Command = ATZ
Password = 1
Baud = 460800



please help me connecting my phone............

---

### Post by muctadir on 2009-11-26
need some help here.........

---

### Post by Saq on 2010-02-05
The problem is solved not to worry it will 100% work u follow these steps (for ubuntu 9.10)
1. Install gnome-ppp and wvdial from the symptic package manager.
2.then run the following commands sequntially-
sudo chown root:dip /usr/sbin/pppd
sudo chmod 4754 /usr/sbin/pppd
sudo chmod 777 /etc/ppp/pap-secrets 
sudo chmod 777 /etc/ppp/peers
3. Now connect your phone and select "Com Port" (option may deffer for mobile phones) then  open NOME ppp from application>>internet
4. Click on the setup tab
5. Click on Detect button and close the window
6. provide phone number, u-name and password for the connection.
(in india GPRS number is *99# and for most of the provider username and password is your mobile number itself)
7. Dial and enjoy the connection.

---

### Post by koanhead on 2010-02-05
This is just a wild guess, and I haven't tried it, but if you look in "Users and Groups" for a group called "wvdial" or similar and then add your username to that group, that might also have solved the problem.
I'm glad your problem is solved, I have only added this for the sake of future searchers.

---

