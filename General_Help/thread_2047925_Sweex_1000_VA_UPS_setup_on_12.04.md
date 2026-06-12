---
title: "Sweex 1000 VA UPS setup on 12.04"
date: 2012-08-25
forum: General Help
---

### Post by hujer on 2012-08-25
I recently purchased Sweex 1000VA (PP210) UPS. Neither Viewpower 2.10 UPS Control SW provided with UPS nor nut monitor are not able to read from UPS. nut does not see it at port 3493. Viewpower claims successfull communiction, but fails to display anything. I sat up /etc/nut/ups.conf as follows:

[sweex]
   driver = genericups upstype=7
   port = auto
   desc = "Sweex 1000VA UPS"

Please, does anybody any experience ho to make this UPS work under ubuntu?

Thanks for any idea, Dag.

***

So, for anybody who purchased Sweex UPS 1000VA and does not know how to operate it under 12.04. After a long reading and lot of workaround I found a way using "blazer_usb" driver. See below a complete instructions how to do it:

At the beginning check, if Your UPS is equipped with Cypress Semiconductor USB to Serial system (it probably coud be equipped with another USB/Serial. Instructions below were tested only for Cypress:

Type:

lsusb

and you have to see something like this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0665:5161 Cypress Semiconductor USB to Serial

Vendor ID should be 0665, ane product ID 5161. If so, continue.

First, install NUT:

sudo apt-get install nut

Next, declare Sweex UPS in /etc/nut/ups.conf to be used with blazer_usb driver:

[sweex]
	driver = blazer_usb
	port = /dev/ttyS0
	desc = "Sweex 1000VA UPS"

The name &#8222;sweex&#8220; in brackets will now identify this UPS througout the system.
 
In /etc/nut/nut.conf set NUT to run in standalone mode. This means, that it is used on the computer to which is UPS connected and the same computer also monitors the UPS:

MODE=standalone

Now bind a listening port to LAN interface to allow upsd (the network daemon) monitor to communicate with the nut server. Add this line to the end of the file /etc/nut/upsd.conf. The number 3493 defines the port on the localhost:

LISTEN 127.0.0.1 3493

Set the permissions for upsd in /etc/nut/upsd.users. All other parameters leave untouched. As &#8222;your_password&#8220; and &#8222;your_ups_password&#8220; I used my root password, it works:

[admin]
password = your_password
action = set
instcmds = ALL

[monuser]
password = your_ups_password
allowfrom = localhost
upsmon master

Configure the UPS monitoring daemon upsmon to be able to communicate with UPS conected to the machine. Modify /etc/nut/upsmon.conf as follows:

MONITOR sweex@localhost 1 upsmon your_password master

Last, modify the permission of nut configuration files to enable NUT to process them:

chown root:nut /etc/nut/*
chmod 640 /etc/nut/*

Now everything should be configured and You can start NUT:

sudo service nut start

Then start driver:

sudo upsdrvctl start

If everything is OK, You should see response like this:

Network UPS Tools - UPS driver controller 2.6.3
Network UPS Tools - Megatec/Q1 protocol USB driver 0.04 (2.6.3)
Supported UPS detected with mustek protocol
Vendor information unavailable
Battery runtime will not be calculated (runtimecal not set)

Finally check status of Your USB:

upsc sweex

and You will see complete USB status:

battery.voltage: 26.10
battery.voltage.nominal: 24.0
beeper.status: enabled
device.type: ups
driver.name: blazer_usb
driver.parameter.pollinterval: 2
driver.parameter.port: /dev/ttyS0
driver.version: 2.6.3
driver.version.internal: 0.04
input.current.nominal: 5.0
input.frequency: 50.1
input.frequency.nominal: 50
input.voltage: 229.2
input.voltage.fault: 229.2
input.voltage.nominal: 220
output.voltage: 229.2
ups.delay.shutdown: 30
ups.delay.start: 180
ups.load: 60
ups.productid: 5161
ups.status: OL
ups.type: offline / line interactive
ups.vendorid: 0665

The line ups.status: OL (near to the end of the file) says, that UPS is running on power line. Disconnect the UPS from power and check it again with upsc sweex. The line should change to ups.status: OB showing, that UPS is running on battery. Now leave the UPS disconnected from power line and see, if it shuts the computer down after several minutes. 

That is all, folks.

---

