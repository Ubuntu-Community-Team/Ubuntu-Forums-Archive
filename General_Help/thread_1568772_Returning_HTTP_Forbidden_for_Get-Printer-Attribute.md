---
title: "Returning HTTP Forbidden for Get-Printer-Attributes"
date: 2010-09-05
forum: General Help
---

### Post by theyranos on 2010-09-05
I recently upgraded my desktop to Lucid, and lost the ability to print from my Mac laptop thanks to [a known bug]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/465916") that broke Bonjour. By [setting the mac to look for CUPS printers]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/465916/comments/3"), I made it so that the server's print queue shows up on my laptop, but I still can't print.

On the server, error_log says:
```

E [05/Sep/2010:19:42:38 -0400] Returning HTTP Forbidden for Get-Printer-Attributes (ipp://10.1.1.100:631/printers/samsung) from 10.1.1.46

```


On the Snow Leopard client machine:
```

D [05/Sep/2010:19:42:38 -0400] [Job 2] Started backend /usr/libexec/cups/backend/ipp (PID 1558)
D [05/Sep/2010:19:42:38 -0400] [Job 2] 1 files to send in job...
D [05/Sep/2010:19:42:38 -0400] [Job 2] STATE: +connecting-to-device
D [05/Sep/2010:19:42:38 -0400] [Job 2] Connecting to 10.1.1.100:631
D [05/Sep/2010:19:42:38 -0400] [Job 2] Connecting to printer...
D [05/Sep/2010:19:42:38 -0400] [Job 2] STATE: -connecting-to-device
D [05/Sep/2010:19:42:38 -0400] [Job 2] Connected to printer...
D [05/Sep/2010:19:42:38 -0400] [Job 2] Connected to 10.1.1.100:631 (IPv4)...
D [05/Sep/2010:19:42:38 -0400] [Job 2] hrDeviceDesc="Unknown"
D [05/Sep/2010:19:42:38 -0400] [Job 2] prtGeneralCurrentLocalization type is 0, expected 2!
D [05/Sep/2010:19:42:38 -0400] [Job 2] Getting supported attributes...
D [05/Sep/2010:19:42:38 -0400] [Job 2] ATTR: auth-info-required=none
D [05/Sep/2010:19:42:38 -0400] [Job 2] Backend returned status 2 (authentication required)
D [05/Sep/2010:19:42:38 -0400] [Job 2] Job held for authentication.
D [05/Sep/2010:19:42:38 -0400] [Job 2] End of messages
D [05/Sep/2010:19:42:38 -0400] [Job 2] printer-state=3(idle)
D [05/Sep/2010:19:42:38 -0400] [Job 2] printer-state-message="/usr/libexec/cups/backend/ipp failed"
D [05/Sep/2010:19:42:38 -0400] [Job 2] printer-state-reasons=none

```

I've placed my server's cups.conf in [http://paste.ubuntu.com/488977/](http://paste.ubuntu.com/488977/). Any insights you might have are appreciated!

---

