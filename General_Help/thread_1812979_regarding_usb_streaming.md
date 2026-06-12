---
title: "regarding usb streaming"
date: 2011-07-27
forum: General Help
---

### Post by angad on 2011-07-27
hi every one

i want to run simple server client programme b/w two ubuntu pc my programmes are running successfully
but my reqirement is to send data over usb.
as it is working corrrect with ethernet port now i want network to run over usb
i have tried configuring usb port as inter face
this is what i ve done

$sudo gedit /etc/network/interfaces

in this file i have written
mapping hotplug
script grep
map usb0
auto usb0
iface usb0 inet static

address 192.168.72.136
netmask 255.255.255.0
gateway 192.168.72.200

$sudo ifup usb0
usb0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
usb0: ERROR while getting interface flags: No such device
Failed to bring up usb0.


waiting for reply
kailash

---

### Post by dim_hyder on 2011-07-27
Hi,

You need to ensure that the USB ethernet adapter is being detected as usb0

From the terminal type:

dmesg | grep usb

Is the adapter even being detected correctly?

Post the output from this command please.

Cheers,

Pete

---

### Post by angad on 2011-07-27
hi pete
thanxx for replying so fast
this is the output
this time my device is my mobile phone
dm365@dm365-desktop:~$ dmesg | grep usb
[    0.121142] usbcore: registered new interface driver usbfs
[    0.121161] usbcore: registered new interface driver hub
[    0.121195] usbcore: registered new device driver usb
[    0.296135] usb usb1: configuration #1 chosen from 1 choice
[    0.296574] usb usb2: configuration #1 chosen from 1 choice
[    0.296866] usb usb3: configuration #1 chosen from 1 choice
[    0.297168] usb usb4: configuration #1 chosen from 1 choice
[    0.297456] usb usb5: configuration #1 chosen from 1 choice
[ 1741.884036] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 1742.061214] usb 3-2: configuration #1 chosen from 1 choice
[ 1742.556907] usbcore: registered new interface driver usb-storage
[ 1742.565305] usb-storage: device found at 2
[ 1742.565309] usb-storage: waiting for device to settle before scanning
[ 1747.565916] usb-storage: device scan complete
[ 1823.960058] usb 3-2: USB disconnect, address 2
[ 2127.620039] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 2127.793195] usb 3-2: configuration #1 chosen from 1 choice
[ 2127.973399] usbcore: registered new interface driver cdc_acm
[ 2167.936059] usb 3-2: USB disconnect, address 3
[ 2196.832041] usb 3-2: new full speed USB device using uhci_hcd and address 4
[ 2197.005200] usb 3-2: configuration #1 chosen from 1 choice
[ 2568.952064] usb 3-2: USB disconnect, address 4
[ 3280.684328] usb 1-4: new high speed USB device using ehci_hcd and address 3
[ 3281.004038] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 3281.148038] usb 3-2: not running at top speed; connect to a high speed hub
[ 3281.176196] usb 3-2: configuration #1 chosen from 1 choice
[ 3281.179485] usb-storage: device found at 5
[ 3281.179488] usb-storage: waiting for device to settle before scanning
[ 3286.177942] usb-storage: device scan complete
[ 3349.656057] usb 3-2: USB disconnect, address 5
[ 3360.192039] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 3360.512039] usb 3-2: new full speed USB device using uhci_hcd and address 6
[ 3360.651283] usb 3-2: not running at top speed; connect to a high speed hub
[ 3360.679433] usb 3-2: configuration #1 chosen from 1 choice
[ 3360.702759] usb-storage: device found at 6
[ 3360.702763] usb-storage: waiting for device to settle before scanning
[ 3365.701185] usb-storage: device scan complete
[ 3450.760090] usb 3-2: USB disconnect, address 6
[ 3459.800040] usb 1-4: new high speed USB device using ehci_hcd and address 5
[ 3460.120037] usb 3-2: new full speed USB device using uhci_hcd and address 7
[ 3460.264047] usb 3-2: not running at top speed; connect to a high speed hub
[ 3460.292197] usb 3-2: configuration #1 chosen from 1 choice
[ 3460.295485] usb-storage: device found at 7
[ 3460.295488] usb-storage: waiting for device to settle before scanning
[ 3465.293938] usb-storage: device scan complete
[ 3495.620084] usb 3-2: USB disconnect, address 7
[ 3507.652036] usb 3-2: new full speed USB device using uhci_hcd and address 8
[ 3507.825182] usb 3-2: configuration #1 chosen from 1 choice
[ 3639.568057] usb 3-2: USB disconnect, address 8
[ 4361.348037] usb 3-2: new full speed USB device using uhci_hcd and address 9
[ 4361.521206] usb 3-2: configuration #1 chosen from 1 choice
[ 4371.168055] usb 3-2: USB disconnect, address 9
[ 4529.244038] usb 3-2: new full speed USB device using uhci_hcd and address 10
[ 4529.417186] usb 3-2: configuration #1 chosen from 1 choice
[ 4537.328061] usb 3-2: USB disconnect, address 10
[ 6829.076035] usb 3-2: new full speed USB device using uhci_hcd and address 11
[ 6829.239190] usb 3-2: configuration #1 chosen from 1 choice
[ 6829.557901] usbcore: registered new interface driver usbserial
[ 6829.558479] usbcore: registered new interface driver usbserial_generic
[ 6829.558483] usbserial: USB Serial Driver core
[ 6829.726326] usb 3-2: pl2303 converter now attached to ttyUSB0
[ 6829.726356] usbcore: registered new interface driver pl2303
[ 6864.560105] usb 3-2: USB disconnect, address 11
[ 6874.184064] usb 3-2: new full speed USB device using uhci_hcd and address 12
[ 6874.347196] usb 3-2: configuration #1 chosen from 1 choice
[ 6874.366201] usb 3-2: pl2303 converter now attached to ttyUSB0
[10044.664061] usb 3-2: USB disconnect, address 12
[10062.964039] usb 3-2: new full speed USB device using uhci_hcd and address 13
[10063.138264] usb 3-2: configuration #1 chosen from 1 choice

thanxx 
kailash

---

### Post by dim_hyder on 2011-07-27
Hi Kailash,

Please can you elaborate more on "my reqirement is to send data over usb".

And out of curiosity, what mobile device are you using?

Cheers,

Pete

---

### Post by angad on 2011-07-27
hi pete
i need to stream some data over usb ie i have some data that is to be send through usb
for this i ve searched a lot and come to a conclusion that it can be possible if out usb port is configured as the network port
with all the protocols same only transmissin media is changed ie ethernet cable to usb cable

there may be somthing missing this is the elobaration
 now what i want to do for testing i have simple tcp server client  running version
if i am using my ethernet port its working properly
now i want to do the same thing with usb .
so what should be the setup
thanxx 
kailash

---

### Post by dim_hyder on 2011-07-27
Hi Kailash,

Thi s link describes a basic setup for IP over USB for android

[http://www.linuxreaders.com/2011/03/09/android-access-internet-from-computer-via-usb/](http://www.linuxreaders.com/2011/03/09/android-access-internet-from-computer-via-usb/)

I hope this helps,

Pete

---

