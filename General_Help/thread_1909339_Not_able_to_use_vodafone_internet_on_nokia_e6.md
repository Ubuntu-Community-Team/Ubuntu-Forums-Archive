---
title: "Not able to use vodafone internet on nokia e6"
date: 2012-01-15
forum: General Help
---

### Post by mritunjay.gec on 2012-01-15
HI,

I tried two ways to connect to internet. one with wvdial and Network manager Mobile broadband connection.

In the first case i installed wvdial and checked with lsusb ...Nokia e6 was listed with the vendor and product id. I used modproe usbserial product= vendor= to enter in the kernel but in the logs it shows me error.


then i created the wvdialconf file and added few entries there ...below is the snapshot of the wvdial conf file..

Studpid Mode = 1
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Init1 = ATZ
Phone = *99#
Modem = /dev/ttySHSF0
Username = 9*********7 <moobile no>
Password = 9**********7<mobile no>
Baud = 460800

the device was detected on ttySHSF0 and ttyACM0 and i tried in both but no success...


i tried **mobile broadband** option and plugged E6. sometimes the broadband got activated and sometimes not. dont know the reason...any idea why it is happening?? very few times it got connected and thus dont know the specific reason ...i am using vodafone connection for internet surfing ...Rs95/- plan...

please provide any solution...


i also tried my friends Tata photon +...i added it in the mobile broadband but it was not detected so not able to invoke it ....also tried it with the wvdial but not able to use it...

i am using Linux 10.04....on dell vostro 1450....


thanks,
Mritun

---

