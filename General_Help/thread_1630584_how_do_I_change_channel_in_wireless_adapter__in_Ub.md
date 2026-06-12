---
title: "how do I change channel in wireless adapter  in Ubuntu 10.10"
date: 2010-11-25
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-11-25
how do I change channel in wireless adapter  in Ubuntu 10.10, I know how to do it in the router thought, there is an extra option in adapter in operating system Ubuntu 10.10 thought, and all the systems

---

### Post by t4thfavor on 2010-11-25
Associate with the SSID of your choosing, and the channel should automatically change. If this is not what is happening, then you may have a problem with your hardware.

Also, please note that this is with the default networkmanager, and not on the commandline.


If your looking to do this on the commandline, I think it's the same, but it's been so long since I have done it that I may be forgetting something.

The commandline wifi config tool is called iwconfig.

I think the syntax is still something like this
```
 iwconfig wlan0 essid 'MySSID' 
```

---

### Post by efflandt on 2010-11-25
The only time you would need to set a channel for wireless is if you are using **ad-hoc** mode to directly connect with another wireless computer or other device, without using a wireless router or AP.

If you are connecting to wireless router or AP (**infrastructure** mode), you will automatically use the channel that is using, so there is no need to set a channel on your computer.

---

### Post by Lukasz Tarkowski on 2010-11-25
Thank you efflandt

---

### Post by t4thfavor on 2010-11-25
No love :(

Yeah, I know I'm a whiner!

---

### Post by Lukasz Tarkowski on 2010-11-27
yeah it is thanks t4thfavor iwconfig wlan0, just wanted to know How I can change the channel, but if no go that's fine.  Thanks

---

### Post by WorMzy on 2010-11-27
```
sudo iwconfig wlan0 channel <CHANNEL NAME>
```

Generally speaking, "auto" works perfectly.

From the man page:

```
       freq/channel
              Set the operating frequency or channel in the  device.  A  value
              below 1000 indicates a channel number, a value greater than 1000
              is a frequency in Hz. You may append the suffix k, M or G to the
              value  (for  example,  "2.46G"  for  2.46 GHz frequency), or add
              enough '0'.
              Channels are usually numbered starting at 1,  and  you  may  use
              iwlist(8)  to  get the total number of channels, list the avail&#8208;
              able frequencies, and display the current frequency as  a  chan&#8208;
              nel. Depending on regulations, some frequencies/channels may not
              be available.
              When using Managed mode, most often the  Access  Point  dictates
              the  channel  and  the driver may refuse the setting of the fre&#8208;
              quency. In Ad-Hoc mode, the frequency setting may only  be  used
              at  initial  cell  creation,  and may be ignored when joining an
              existing cell.
              You may also use off or auto to let the card pick  up  the  best
              channel (when supported).
              Examples :
                   iwconfig eth0 freq 2422000000
                   iwconfig eth0 freq 2.422G
                   iwconfig eth0 channel 3
                   iwconfig eth0 channel auto

```

---

