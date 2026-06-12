---
title: "PulseAudio couldn't find Bluetooth headset"
date: 2010-01-09
forum: General Help
---

### Post by giskar on 2010-01-09
Hi guys, I have connected BT headset (used Blueman) and I try to bring all sounds to it device. I take this instruction [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)
Everything goes fine until the step 16:

```

If not already connected, click on the Connect button to connect to your local PulseAudio server. When connected, you will see details about it listed.

```

As I understand, I need to connect to default server and I do it. Furthermore, I need to go to the Device tab and there I would see my BT headset...but it is not there:sad:


```

cat ~/.asoundrc

pcm.btheadset {
        type bluetooth
        device 00:33:44:DD:EE:FF    # MAC of my BT headset
        profile “auto”
}

```

Who's know what problem?  File .asoundrc must locate in user home directory or in root directory?

---

### Post by giskar on 2010-01-09
can anybody help my?

---

