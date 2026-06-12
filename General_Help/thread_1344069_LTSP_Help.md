---
title: "LTSP Help"
date: 2009-12-02
forum: General Help
---

### Post by sgardne on 2009-12-02
I have brought up an Ubuntu LTSP server on my network. Initially, I had it working with 2 network cards, but then I realized it was handing out DHCP on my network, and I didn't want that, so I disabled the 2ndary NIC and gave my DHCP server the next-server and filename options which seems to be working, however now I never get to the login screen. It would appear that my thin client is connecting to the server and downloading the image. I see the black screen with the white Ubuntu logo for a few seconds, then the screen goes black and nothing happens. I'm pretty new to the whole LTSP scene, so I have no idea what logs to check or how to go about troubleshooting this. 

It was working fine with the second NIC handing out DHCP to me, but now with my DHCP server pointing me to the LTSP server, it doesn't. Can anyone help?

Thanks!


Edit: LTSP server is v9.10 if that matters. Basically haven't done anything but install the LTSP mode from the alternate install disk.

---

### Post by gmjs on 2009-12-02
I've never set up LTSP with an existing DHCP server, but perhaps the 'root path' needs setting on your DHCP server too?

I found the following code that you could add after the 'filename' option in dhcpd.conf for the private interface (although I'm not sure if the path applies to the latest version of LTSP):

```
option root-path "/opt/ltsp/i386";
```

Sorry I can't be of more help!

---

### Post by sgardne on 2009-12-02
Well, I think it's actually finding the file, so I don't think the path is an issue. It just doesn't seem to get all the way to the login screen. 

I'm trying to figure out how to disable the splash screen so I can look at the messages now. Hopefully that will help.

---

### Post by sgardne on 2009-12-02
Okay, I think this may have actually been network related somehow, although I'm not sure. I changed the IP of the LTSP server and changed the DHCP option next-server to match, and now it works again. 

Thanks for looking!

---

