---
title: "Can't get Samsung SCH-r631 (cricket) phone to mount"
date: 2012-02-21
forum: General Help
---

### Post by fuzzman17 on 2012-02-21
I can't get my cell phone to mount under Ubuntu 11.10 or to be recognised by Bitpim. The computer will try and use it as a modem. Here is the info I have so far and what I've done.

                                  When trying to connect to the pc as a mass storage device usb-devices shows this. Bitpim will not find the phone automatically but will let me choose it manually.
 

 T:  Bus=02 Lev=01 Prnt=01 Port=06 Cnt=04 Dev#= 19 Spd=12  MxCh= 0 
 D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=05c6 ProdID=1000 Rev=00.00 
 S:  Manufacturer=Qualcomm, Incorporated 
 S:  Product=USB MMC Storage 
 S:  SerialNumber=000000000002 
 C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA 
 I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none) 
 kevin@Main-MS-7309:~$
 

 When the computer is trying to use the phone as a modem Bitpim will find it but not access it  and usb-devices shows this.
 

 T:  Bus=02 Lev=01 Prnt=01 Port=06 Cnt=04 Dev#= 15 Spd=12  MxCh= 0 
 D:  Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=04e8 ProdID=6640 Rev=00.00 
 S:  Manufacturer=SAMSUNG Electronics Bo.,Ltd. 
 S:  Product=SAMSUNG CDMA Technologies 
 C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm 
 I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm 
 I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=qcaux
 

 dmesg gives me this while phone is trying to connect to the pc as mass storage device.
 

 [82193.256029] usb 2-7: new full speed USB device number 17 using ohci_hcd 
 [82193.465406] usb 2-7: unable to read config index 0 descriptor/all 
 [82193.465410] usb 2-7: can't read configurations, error -62 
 [82193.524025] hub 2-0:1.0: unable to enumerate USB device on port 7 
 [82195.004027] usb 2-7: new full speed USB device number 19 using ohci_hcd 
 [82195.229436] scsi9 : usb-storage 2-7:1.0
 

 Sudo fdisk -l does not show phone as being mounted.  
 

 To get this far I created a file using the instructions on the bitpim site and set it up as a single user machine found here. [http://www.bitpim.org/help/](http://www.bitpim.org/help/)
 

 
[LIST]
[*]**Create ****/etc/udev/rules.d/60-cell.rules**
[/LIST]
 SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end" # LG Phone SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", GROUP="cellusers", MODE="0660" LABEL="cell_rules_end" 1004 and 6000 should of course be replaced with the relevant *VID* and *PID*. (For the Sanyo SCP-3100 the VID/PID is 0474/071f).
 If you have a single user machine, you may find it easier to use a mode of 0666 and leave off the GROUP item.  
  # LG Phone was changed to # Samsung Phone and the proper VID/PID where entered.  In the next section under auto port and phone detection it says.
**Auto Port and Phone Detection**

 BitPim can now auto-detect known USB devices (cell phones with USB  cables) being connected to the computer (it is not aware if a device is  disconnected from the computer).  This feature is only available on  systems runing udev version 095 or later (udevinfo -V) when BitPim is installed.  
In order to take advantage of this feature, make sure that the followings are in place: 

[LIST]
[*]File /etc/udev/rules.d/60-bitpim.rules exists.
[*]File /usr/bin/bpudev exists.
[*]Group cellusers exists and you belong to that group.
[/LIST]
  When a known device is connected, this feature sets the the device group to cellusers, permission to 0664, and initiates the BitPim phone detection process.  The end result is that BitPim will be able to: 

[LIST=1]
[*]Detect that a known device is connected,
[*]Set the appropriate group and permission for that device,
[*]Try to detect the phone model of that device.
[/LIST]
The file bpudev does exist but it's in /lib/udev.
The phone will mount as a mass storage device on a computer using windows 7.
any ideas on what to try next?

---

