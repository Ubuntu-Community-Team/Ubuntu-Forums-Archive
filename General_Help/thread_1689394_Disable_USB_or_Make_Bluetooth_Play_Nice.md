---
title: "Disable USB or Make Bluetooth Play Nice"
date: 2011-02-16
forum: General Help
---

### Post by Percius on 2011-02-16
I have a new Asus U41JF laptop... I installed a new Intel 6300 ABGN (2&5ghz) wifi card. (There are 39 2.4ghz access points in my area so throughput is awful).

The default behavior of this card is that it detects networks, but does not succeed at connecting (regardless of encryption). In Windows this problem was overcome by disabling the bluetooth. Updating to the newest driver seems to have eliminated the need to disable it.

In Linux everything works if I disable the Bluetooth in Bios. However I don't want to do that. Blacklisting the modules (bluetooth, btusb, sco) does not seem to fix the issue. Using the widgit and disabling bluetooth has no result. Toggling the wireless network also has no effect. reloading the iwlagn module does not seem to make a difference either. 

I want bluetooth in windows, but have no need for it in linux. As a result I am looking for a way to either fix the root problem or disable bluetooth via software.

Note: The bluetooth device is USB, but Internal... lsusb simply identifies it as AsusTek. 
Note: This issue was not existant with the origional wifi card. (which unfortunately didn't support 5ghz).

---

