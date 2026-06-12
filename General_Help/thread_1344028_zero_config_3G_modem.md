---
title: "zero config 3G modem"
date: 2009-12-02
forum: General Help
---

### Post by andres-bracho on 2009-12-02
Hi,

I have a zero config alcatel x060 usb modem (one of those that use the mobile phone network to connect to internet).

In ubuntu 9.10, how can I configure it and make it work?

Thanks in advance

---

### Post by halj32 on 2009-12-02
have a look here
[http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html](http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html)




[ How to get a Huawei HSDPA USB modem working in a new install of Karmic ]


Open up places, Computer & if you see a virtual CD ROM & HUAWEI SD Storage (for the microSD card if your modem Has one

right mouse click on the Virtual CD ROM (you don't need it as there windows drivers) & select safety remove device)

then when the HUAWEI SD Storage device & the virtual CD ROM has Gone , close the computer browser box


open a terminal up

Applications , Accessory , Terminal

then copy & paste these following commands (there just to get your modem to be seen by network-manager)

sudo rmmod usb-storage

[enter your user password if asked for it] then can follow on with the rest without entering your user password

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

or

sudo modprobe usbserial vendor=0x12d1 product=0x1003 [If the first code doesn't work]


Then lastly

sudo pppd ttyUSB0

& don't forget to close the terminal box when finished with it


[Dialer three]
Phone =3D *99***1#
Username =3D 
Password =3D 
Stupid Mode =3D 1
Dial Command =3D ATDT
Modem =3D /dev/ttyUSB2
Baud =3D 460800
Init2 =3D ATZ
Init3 =3D ATE0V1&D2&C1S0=3D0+IFC=3D2,2
ISDN =3D 0
Modem Type =3D Analog Modem
Init5 =3DAT+CGDCONT=3D1,"IP","three.co.uk";
Modem Type =3D USB Modem

sudo depmod -a
sudo modprobe wl
sudo iwlist scan


then when you goto Network-Manager & right mouse , click on edit connections, Mobile broadband, Add a connection , your modem will now be showing

---

### Post by andres-bracho on 2009-12-02
Wow, thank you, I'll try it as soon as I arrive home tonight...  : )

---

### Post by andres-bracho on 2009-12-03
Last night I tried your recommendations, and this is what happened...

andres@MegaMovil:~$ sudo rmmod usb-storage
[sudo] password for andres: 
ERROR: Module usb_storage is in use

I continue with your recommendation (I know, but I was just trying) and...
andres@MegaMovil:~$ sudo modprobe -r option
andres@MegaMovil:~$ sudo modprobe -r usbserial
andres@MegaMovil:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1001
andres@MegaMovil:~$ sudo pppd ttyUSB0
pppd: unrecognized option 'ttyUSB0'
pppd version 2.4.5
Usage: pppd [ options ], where options are:
    <device>    Communicate over the named device
    <speed>        Set the baud rate to <speed>
    <loc>:<rem>    Set the local and/or remote interface IP addresses.  Either one may be omitted.
    asyncmap <n>    Set the desired async map to hex <n>
    auth            Require authentication from peer
        connect <p>     Invoke shell command <p> to set up the serial line
    crtscts        Use hardware RTS/CTS flow control
    defaultroute    Add default route through interface
    file <f>    Take options from file <f>
    modem        Use modem control lines
    mru <n>        Set MRU value to <n> for negotiation
See pppd(8) for more options.
andres@MegaMovil:~$


What can I do?

If I can make this work, I'll finally remove Windows from my life...  :p

---

### Post by halj32 on 2009-12-03
right click on your conection manager
new conection
click on the modem
new conection

3 Internet    connection name

*99#          number

3internet     APN

save
you should now be able to conect
or try Linux Mint 8

---

### Post by andres-bracho on 2009-12-03
This was already done, even before using this modem... the system just don't see the modem...  : (

---

