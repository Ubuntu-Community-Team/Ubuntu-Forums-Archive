---
title: "Emable Bluetooth on Lenovo E320"
date: 2012-09-15
forum: General Help
---

### Post by mercmobily on 2012-09-15
Hi,

I would love to enable Bluetooth in my new Lenovo E320. I have a kid coming (still in a belly right now!), and would love him to hear some music... and have trouble without Bluetooth!

Under "Bluetooth settings", I have a "Bluetooth is disabled by hardware switch".

Using rfkill is not helping:


# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
# rfkill unblock all
#
# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes

Still hard blocked.

I tried with proc:

# cd /proc/acpi/ibm
# echo "enable" > bluetooth

But no. In fact, it made it even worse...

# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes

I tried fn+F9 (the little antenna sign), nothing. 
The laptop does NOT have a hardware switch, if you are wondering. I am now just concerned that the hardware switch is something that needs to be done via software... that is, using Windows (!) plus original drivers (!!).

Any hints anybody?

Merc.

---

### Post by mercmobily on 2012-09-15
Hi,

Update: I tried more with proc:


:/sys/devices/platform/thinkpad_acpi# echo 1 > bluetooth_enable 
-su: echo: write error: Operation not permitted
:/sys/devices/platform/thinkpad_acpi# cat bluetooth_enable 
0
:/sys/devices/platform/thinkpad_acpi# echo 1 > hotkey_radio_sw 
-su: hotkey_radio_sw: Permission denied

Ugh!

Merc.

---

### Post by mercmobily on 2012-09-15
Hi,

I found something very obscure on the net which suggested to reset Bios settings to their defaults (the only thing I ever did was swapping CTRL with FN, since anybody sane would want that!).

Well, it worked!

Now I live in fear of it going away again :D

Merc.

---

