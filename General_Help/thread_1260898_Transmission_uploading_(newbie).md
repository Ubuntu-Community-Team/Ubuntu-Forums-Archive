---
title: "Transmission uploading (newbie)"
date: 2009-09-08
forum: General Help
---

### Post by irishbreakfast on 2009-09-08
Why is Transmission uploading when I have not enable port forwarding?

From reading the Help and the Forum I thought that I had to enable port forwarding for uploading to occur because of our router. I haven't and it is - so I am missing something.

Please explain.

---

### Post by P4man on 2009-09-08
You don't need portforwarding to upload.
(You probably dont even need to do any portforwarding at all, if your router supports UPnP).

Transmission, or any bittorrent client will always upload, its how BT works. You can reduce the upload rate if it interferes with your browsing, set it to  ~half your connection speed. Preferences > speed > Speed limits.

---

### Post by 3rdalbum on 2009-09-08
To clarify:

If you haven't manually forwarded ports from your router, then you need to turn on UPnP Port Forwarding in Transmission, and make sure that UPnP is turned on in your router's configuration.

If Transmission is not uploading, it is because the Bittorrent tracker has not provided your computer's IP address to anyone who wants to download. Or you might have "Limit upload speed" turned on, and the speed limit set to zero kilobytes per second.

---

### Post by lovinglinux on 2009-09-08
Port forwarding is only required for accepting incoming connection requests and does not prevent outgoing connections, neither downloading/uploading.

Anyways, I'm writing a BitTorrent tutorial that explains this a little bit further. The tutorial is still under development, but what you want to know is already well explained.

Please visit - [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by irishbreakfast on 2009-09-08
Thank you very much lovinglinux!  I've had a skim and I think I understand now. 

And btw, you answered my unasked wish. When I was writing my post I was thinking that I need to find 'The Idiot's Guide to BitTorrent' (or equivalent). And you delivered!

Cheers

---

### Post by lovinglinux on 2009-09-09
> **irishbreakfast said:**
> Thank you very much lovinglinux!  I've had a skim and I think I understand now. 

And btw, you answered my unasked wish. When I was writing my post I was thinking that I need to find 'The Idiot's Guide to BitTorrent' (or equivalent). And you delivered!

Cheers

:) You are welcome. I still need to finish it. After a very heavy storm yesterday, I was unable to access the Internet until now, due to the lack of electricity for 28 hours ](*,)

---

