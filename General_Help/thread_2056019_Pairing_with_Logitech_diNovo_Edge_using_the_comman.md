---
title: "Pairing with Logitech diNovo Edge using the command line?"
date: 2012-09-10
forum: General Help
---

### Post by azzid on 2012-09-10
I recently installed ubuntu 12.04 from the **mini.iso**.

Since the install is rather minimal the available gui tools are somewhat limited, which has forced me to try to pair my computer with its bluetooth keyboard from the command line.

As I read man-pages, google and experiment with some trial and error it strikes me as a unlikely complicated thing to do. This than makes me believe I'm doing something fundamentally wrong.

It also seems alot has changed in bluetoothd over the last couple of years as most of the suggested techniques I find seem outdated.

So could someone please explain how one is supposed to do it correctly in Ubuntu 12.04?

I have read the [bluetoothd manpage]("http://manpages.ubuntu.com/manpages/precise/man8/bluetoothd.8.html") and the [hcitool manpage]("http://manpages.ubuntu.com/manpages/precise/man1/hcitool.1.html").

If I do something like this:
```
$ sudo hcitool scan
Scanning ...
	00:07:61:7F:CD:D5	Logitech diNovo Edge

```
I get the MAC of the keyboard, so the blutooth device seems to be working.

Running the following without pushing connect on the keyboard:
```
$ sudo hcitool cc 00:07:61:7F:CD:D5
Can't create connection: Input/output error
```

But as soon as I put the keyboard in 'promiscuous mode' it works better:
```
$ sudo hcitool cc 00:07:61:7F:CD:D5
$
``` 

But the keyboard keeps blinking, and I guess a pin needs to be supplied somewhere.

Arguments like **auth** and **key** looks promising, but their documentation is quite weak:
```
$ sudo hcitool auth --help
Usage:
	auth <bdaddr>

```
```
$ sudo hcitool key --help
Usage:
	key <bdaddr>

```

Files like **/etc/bluetooth/pin** and **/etc/bluetooth/hcid.conf** that are frequently mentioned in my google hits no longer exist:
```
$ ls /etc/bluetooth
audio.conf  input.conf  main.conf  network.conf  proximity.conf  rfcomm.conf  serial.conf

```

So, to ask the question again: What is it that I'm missing?

---

### Post by azzid on 2012-09-10
After reading [here]("https://help.ubuntu.com/community/BluetoothSetup") I tried the following:

```
$ sudo apt-get install python-gobject python-dbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-dbus is already the newest version.
Suggested packages:
  python-gobject-2-dbg
The following NEW packages will be installed:
  python-gobject python-gobject-2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 243 kB of archives.
After this operation, 1 162 kB of additional disk space will be used.
Get:1 http://se.archive.ubuntu.com/ubuntu/ precise/main python-gobject-2 amd64 2.28.6-10ubuntu1 [240 kB]
Get:2 http://se.archive.ubuntu.com/ubuntu/ precise-updates/main python-gobject all 3.2.2-1~precise [2 468 B]
Fetched 243 kB in 0s (622 kB/s)             
Selecting previously unselected package python-gobject-2.
(Reading database ... 61592 files and directories currently installed.)
Unpacking python-gobject-2 (from .../python-gobject-2_2.28.6-10ubuntu1_amd64.deb) ...
Selecting previously unselected package python-gobject.
Unpacking python-gobject (from .../python-gobject_3.2.2-1~precise_all.deb) ...
Setting up python-gobject-2 (2.28.6-10ubuntu1) ...
Setting up python-gobject (3.2.2-1~precise) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

```
$ sudo bluez-simple-agent hci0 00:07:61:7F:CD:D5
RequestPinCode (/org/bluez/550/hci0/dev_00_07_61_7F_CD_D5)
Enter PIN Code: 1111
Release
New device (/org/bluez/550/hci0/dev_00_07_61_7F_CD_D5)

```

```
$ sudo bluez-test-device trusted 00:07:61:7F:CD:D5 yes
$ sudo service bluetooth restart
bluetooth stop/waiting
bluetooth start/running, process 3511

```

But still no functioning keyboard.

It did some kind of pairing though, because when I try again:
```
$ sudo bluez-simple-agent hci0 00:07:61:7F:CD:D5
Creating device failed: org.bluez.Error.AlreadyExists: Already Exists

```

---

### Post by azzid on 2012-09-10
Also, as [this]("http://blog.neolocus.com/2012/04/ubuntu-12-04-lts-precise-pangolin-and-logitech-dinovo-keyboard-issue/") issue tend to clutter my google searches I'd like to point out that I'm not using the diNovo dongle.
My computer has a builtin bluetooth receiver which worked flawlessly until I reinstalled and lost the gui.

---

### Post by azzid on 2012-09-12
Got the tip to use hcidump to get a verboser glimpse of what's happening/failing.

This is what happens when I try to do **hcitool cc 00:07:61:7F:CD:D5**:
```
$ sudo hcidump
HCI sniffer - Bluetooth packet analyzer ver 2.2
device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 00:07:61:7F:CD:D5 ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
> HCI Event: Vendor (0xff) plen 2
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Vendor (0xff) plen 2
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 21 bdaddr 00:07:61:7F:CD:D5 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 21
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 21
    Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:07:61:7F:CD:D5 mode 2 clkoffset 0x0000
> HCI Event: Vendor (0xff) plen 2
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Vendor (0xff) plen 2
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:07:61:7F:CD:D5 name 'Logitech diNovo Edge'
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 21 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 21 reason 0x16
    Reason: Connection Terminated by Local Host
```

---

