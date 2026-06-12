---
title: "belkin router storage help"
date: 2010-11-02
forum: General Help
---

### Post by paulridley on 2010-11-02
Hope you can help.

Running xubuntu on a laptop and desktop, wirelessly and wired respectivly.

Connect to a Belkin Router F5D8635-4v1. 

This device has a USB port to allow a External drive to be used throughout the network for storage / sharing.
Conncection is via //192.168.2.1/san where san is the device name.  Works perfectly in a MS environment, but the virus are killing me.

How do i connect to this device to RWX files on this device in ubuntu. 

A past post by a member suggestion failed when I installed Nautilus, but the application does not come up under applications or places. A quick check on the net, and it seems other people may also be having problems with Nautilus and Xubuntu?

Is there a way to connect via a terminal screen? or any other suggestions. 

Belkin of course don't support Linux despite the fact thats what they build on!

Thanks

Paul

---

### Post by tredegar on 2010-11-02
It should work fine as it is.
See this link: 
[http://linuxology.blogspot.com/2009/07/connecting-ubuntu-to-belkin-n-router.html](http://linuxology.blogspot.com/2009/07/connecting-ubuntu-to-belkin-n-router.html)
For a HOWTO :)

---

### Post by gandaran on 2010-11-02
I have a sitecom usb storage router and the first time I use it I have to connect from the places menu » connect to server » windows shares, fill in the storage share name in server field (in my case is /storage/usb1-c) then hit the connect button, (no need to install anything) thats all! after the storage share opens in nautilus I bookmark it so next time I just click the bookmark to open the storage share.
hope this helps.

---

### Post by gandaran on 2010-11-04
if the above did not work try [COLOR="Blue"]smb://192.168.2.1/[/COLOR] (your router ip, if that ip is correct)
I tried mine with the ip and it also worked for me.

---

