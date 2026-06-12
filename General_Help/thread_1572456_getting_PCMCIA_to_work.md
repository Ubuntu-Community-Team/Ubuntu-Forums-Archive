---
title: "getting PCMCIA to work?"
date: 2010-09-11
forum: General Help
---

### Post by tubunu on 2010-09-11
I would like to ask for help on getting a PCMCIA card to work on Lubuntu.

I have an old laptop (P3, 192 RAM) with Windows XP installed on it, but it is sooo slow, I decided to switch to Lubuntu. However, I cannot figure out how to enable the PCMCIA card after a fresh Lubuntu install. I've searched the Internet in and out for any tips and advice, but I couldn't find anything... :(

Thank you in advance.

---

### Post by plucky on 2010-09-11
> **tubunu said:**
> I would like to ask for help on getting a PCMCIA card to work on Lubuntu.

I have an old laptop (P3, 192 RAM) with Windows XP installed on it, but it is sooo slow, I decided to switch to Lubuntu. However, I cannot figure out how to enable the PCMCIA card after a fresh Lubuntu install. I've searched the Internet in and out for any tips and advice, but I couldn't find anything... :(

Thank you in advance.

Look [Here](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and see if your card is supported or if you need to use ndiswrapper to load the windows driver.

Post output of ```
lspci
``` with the pcmcia card installed.

---

### Post by tubunu on 2010-09-12
```
@lucid:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0a.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
00:0d.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

My **PCMCIA card** is called **Globetrotter EDGE**. Here it is displayed as 3Com (I think it's this one)

Here's the output of lsusb though I don't even know if it's needed for this card:
```
@lucid:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by plucky on 2010-09-13
> 00:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)


That is the wired ethernet connection.

Your card is not showing up in that list.

Try removing the card and running the **lspci** command again and see if the list is the same or not.

---

### Post by tubunu on 2010-09-13
After running the command the second time, the list is the same. If the Winmodem entry is not the one, then it's not showing. 00:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)

But here is what I get when I remove and insert the PCMCIA card and run **dmesg**:

```

**dmesg output**
[  123.756493] eth0:  setting full-duplex.
[  123.756650] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  134.288066] eth0: no IPv6 routers present
[ 1145.722515] pcmcia_socket pcmcia_socket1: pccard: card ejected from slot 1
[ 1192.032119] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
[ 1192.032320] pcmcia 1.0: pcmcia: registering new device pcmcia1.0
[ 1192.761948] 1.0: [COLOR="Red"]ttyS2[/COLOR] at I/O 0x3e8 (irq = 3) is a 16550A

```

So it is recognized. Now, how to make Lubuntu want to see it?

---

### Post by tubunu on 2010-09-13
Here's what I've done so far (trial and error) and I have *some success* but I still don't know how to get the PCMCIA to work: 

* created the following 3 scripts - copied from other sites, of course! ;)

1. in /etc/ppp/peers/iplus:
```
noauth
connect "/usr/sbin/chat -v -f /etc/ppp/iplus-connect"
disconnect "/usr/sbin/chat -v -f /etc/ppp/iplus-disconnect"
debug
/dev/ttyS[COLOR="Red"]2[/COLOR]
115200
defaultroute
crtscts
lock
local
nodetach
usepeerdns
lcp-echo-failure 4
lcp-echo-interval 65535
```

2. in etc/ppp/iplus-connect:
```
TIMEOUT 600
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting GPRS connect script\n'
"" 'AT+CFUN=1,1'
"" 'AT+CPIN=0000' [COLOR="red"][entered my card PIN code here][/COLOR]
OK 'ATE1\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d'
SAY 'Setting APN\n'
OK 'AT+CGDCONT=1,"IP","www.plusgsm.pl"'
ABORT 'NO CARRIER'
SAY 'Dialing...\n'
OK 'ATD*99***1#'
```


3. in /etc/ppp/iplus-disconnect:
```
"" "\K"
"" "+++ATH0"
SAY "GPRS Disconnected."
```


Then, in Terminal:
```
sudo pppd call iplus
```

[COLOR="Red"]And I SWEAR it worked for a brief moment!! That is, I saw the DNS, IP etc,[/COLOR] but since I couldn't see the connection in Network Manager, I decided to run this command again after restarting the Terminal, and now it doesn't want to work. :( I wish I had saved the original output from the Terminal to paste here...

So now after typing this I get:

```
@lucid:~$ comgt -d /dev/ttyS2
SIM ready
Waiting for Registration..(120 sec max)
Registered on Home network: "Plus GSM"
Signal Quality: 36,99

```

But when I try to run the script now, I get this:
```
@lucid:~$ sudo pppd call iplus
[sudo] password for user: 
Starting GPRS connect script
Setting APN
Script /usr/sbin/chat -v -f /etc/ppp/iplus-connect finished (pid 6836), status = 0x6
Connect script failed
```


So I'm back to square one. I don't know how to enable the modem and what to control it with. (I wouldn't like to do it in the Terminal)

I hope this is getting me somewhere. Thanks for any insight.

---

### Post by tubunu on 2010-09-15
OK, I got it to work by installing gnome-ppp and setting up the connection in it in addition to what I've done so far.

---

