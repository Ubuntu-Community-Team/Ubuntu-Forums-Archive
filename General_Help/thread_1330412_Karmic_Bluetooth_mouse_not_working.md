---
title: "Karmic Bluetooth mouse not working"
date: 2009-11-18
forum: General Help
---

### Post by teddmeister2 on 2009-11-18
I have recently bought a barebones kit and upgraded my wifes computer to Karmic.  I'm using a bluetooth dongle and bluetooth mouse that work on a hardy computer (sometimes initial pairing requires sudo hidd).  I've been trying to get this to work with my wifes new computer with karmic.  Here are the output of dmesg, hcitool con, and hidd --show (in reverse order):

```
00:07:61:66:6D:F7 Logitech Bluetooth Mouse [046d:b002] connected 

```

```
Connections:
	< ACL 00:07:61:66:6D:F7 handle 42 state 1 lm MASTER 
```

```
[10591.465318] input: Logitech Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:42/input10
[10591.465459] generic-bluetooth 0005:046D:B002.0008: input,hidraw7: BLUETOOTH HID v48.09 Mouse [Logitech Bluetooth Mouse] on 00:1B:DC:0F:FA:30

```

Does anyone have any ideas on how I can fix this?

---

### Post by teddmeister2 on 2009-11-18
Is the MAC address discrepancy to be expected?  Or is that what's wrong?

---

### Post by teddmeister2 on 2009-11-24
Can anyone help me?

---

### Post by teddmeister2 on 2009-11-25
bump

---

### Post by supradave on 2009-12-04
If your mouse isn't working but your keyboard is, you can do an Alt-F1 and arrow over to System, go down to Preferences and select Bluetooth and see if you can pair through there.  Of course, if you have a wired mouse, you can do it that way.

I have a Logitech Bluetooth mouse and it sometimes disconnects itself and I have to do the above.  Why?  I don't know.

---

