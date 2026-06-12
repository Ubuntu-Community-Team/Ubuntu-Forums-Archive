---
title: "SerialToUsb connection"
date: 2010-10-12
forum: General Help
---

### Post by Xtermkep on 2010-10-12
Hi 
I have been struggeling for the past few day getting my serial->usb connection up running. 
The device im trying to hook up runs on a normal RS-232 connection through at serial -> usb convertor and into the pc. 

The device is active and will keep spitting out data, like a GPS does. The device is working as i got it up running in windows using the next,next,yes,ok,finish, run 

I suppose plug and pray does work sometimes. However i do not want to work with this device in windows.

so trying to get this running in ubuntu this is what i have done so far:

lsusb finds my device:
Bus 006 Device 007: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

Ive read on other posts around that they had to remove something called brltty as it may cause some interferance with ftdi. So all the brltty packages are removed.

ive tried to use:
 *cu* -l /dev/*ttyUSB0* -s 115200 

now when i do that it say 
connected.

then notting what so ever happends. 
In the documentation that is the correct speed at which the device send information on. 

my 
dmesg output (I removed some of it as i auto mount some hds)
```

  17.168973] Registered led device: iwl-phy0::radio
[   17.168990] Registered led device: iwl-phy0::assoc
[   17.169041] Registered led device: iwl-phy0::RX
[   17.169054] Registered led device: iwl-phy0::TX
[   17.180891] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.182071]   alloc irq_desc for 31 on node -1
[   17.182073]   alloc kstat_irqs on node -1
[   17.182105] tg3 0000:09:00.0: irq 31 for MSI/MSI-X
[   17.217841] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.259972] apm: BIOS not found.
[   17.479701] ppdev: user-space parallel port driver
[   17.598361] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   18.820824] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   18.820826] tg3: eth0: Flow control is on for TX and on for RX.
[   18.940900] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.552048] CE: hpet increasing min_delta_ns to 15000 nsec
[   29.580050] eth0: no IPv6 routers present
[ 1848.760301] usb 6-2: USB disconnect, address 3
[ 1848.760740] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 1848.760773] ftdi_sio 6-2:1.0: device disconnected
[ 1883.720185] usb 6-2: new full speed USB device using uhci_hcd and address 4
[ 1883.903318] usb 6-2: configuration #1 chosen from 1 choice
[ 1883.908128] ftdi_sio 6-2:1.0: FTDI USB Serial Device converter detected
[ 1883.908182] usb 6-2: Detected FT232BM
[ 1883.908187] usb 6-2: Number of endpoints 2
[ 1883.908193] usb 6-2: Endpoint 1 MaxPacketSize 64
[ 1883.908199] usb 6-2: Endpoint 2 MaxPacketSize 64
[ 1883.908204] usb 6-2: Setting MaxPacketSize 64
[ 1883.909346] usb 6-2: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2011.200248] usb 6-2: USB disconnect, address 4
[ 2011.200642] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2011.200685] ftdi_sio 6-2:1.0: device disconnected
[ 2012.680080] usb 6-2: new full speed USB device using uhci_hcd and address 5
[ 2012.859589] usb 6-2: configuration #1 chosen from 1 choice
[ 2012.865315] ftdi_sio 6-2:1.0: FTDI USB Serial Device converter detected
[ 2012.865370] usb 6-2: Detected FT232BM
[ 2012.865375] usb 6-2: Number of endpoints 2
[ 2012.865381] usb 6-2: Endpoint 1 MaxPacketSize 64
[ 2012.865386] usb 6-2: Endpoint 2 MaxPacketSize 64
[ 2012.865391] usb 6-2: Setting MaxPacketSize 64
[ 2012.866348] usb 6-2: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2022.856164] usb 6-2: USB disconnect, address 5
[ 2022.856526] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2022.856561] ftdi_sio 6-2:1.0: device disconnected
[ 2053.604086] usb 6-2: new full speed USB device using uhci_hcd and address 6
[ 2053.781914] usb 6-2: configuration #1 chosen from 1 choice
[ 2053.787628] ftdi_sio 6-2:1.0: FTDI USB Serial Device converter detected
[ 2053.787684] usb 6-2: Detected FT232BM
[ 2053.787689] usb 6-2: Number of endpoints 2
[ 2053.787695] usb 6-2: Endpoint 1 MaxPacketSize 64
[ 2053.787700] usb 6-2: Endpoint 2 MaxPacketSize 64
[ 2053.787705] usb 6-2: Setting MaxPacketSize 64
[ 2053.792083] usb 6-2: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2168.680132] usb 6-2: USB disconnect, address 6
[ 2168.680504] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2168.680544] ftdi_sio 6-2:1.0: device disconnected
[ 2175.120057] usb 6-2: new full speed USB device using uhci_hcd and address 7
[ 2175.297705] usb 6-2: configuration #1 chosen from 1 choice
[ 2175.303575] ftdi_sio 6-2:1.0: FTDI USB Serial Device converter detected
[ 2175.303632] usb 6-2: Detected FT232BM
[ 2175.303637] usb 6-2: Number of endpoints 2
[ 2175.303643] usb 6-2: Endpoint 1 MaxPacketSize 64
[ 2175.303649] usb 6-2: Endpoint 2 MaxPacketSize 64
[ 2175.303654] usb 6-2: Setting MaxPacketSize 64
[ 2175.304596] usb 6-2: FTDI USB Serial Device converter now attached to ttyUSB0
[ 5851.433399] CE: hpet increasing min_delta_ns to 22500 nsec

```Hopefully some out there might have some answers.

Cheers
XTermkep

---

### Post by captainron on 2010-10-25
Can you tell what software your using to run the gps download and what model gps u use. I use oziexplorer and I know that it only expects garmin etrex to use serial hence it looks to ttyS2 (comm3). one work around it to:
 sudo ln -sb /dev/ttyUSB0 /dev/ttyS2
This temp worked for me

also check what interface your gps outputs ie nmea etc

---

