---
title: "Kubuntu Adobe Reader Install Error"
date: 2011-05-04
forum: General Help
---

### Post by Rayray333 on 2011-05-04
I made the switch from Gnome to KDE and did a fresh install of Kubuntu 10.10. When going through my list of what to install, I cam across and error with Adobe Reader. It says and I quote... "Sorry, an error has occurred. And error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator."

These are the commands I ran in Konsole....
```
rayray@ANONYMOUS:~$ wget http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin
--2011-05-04 17:18:11--  http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin
Resolving airdownload.adobe.com... 65.125.72.11, 65.125.72.35
Connecting to airdownload.adobe.com|65.125.72.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15980996 (15M) [application/octet-stream]
Saving to: `AdobeAIRInstaller.bin.1'

100%[========================================>] 15,980,996   719K/s   in 25s     

2011-05-04 17:18:36 (632 KB/s) - `AdobeAIRInstaller.bin.1' saved [15980996/15980996]

rayray@ANONYMOUS:~$ chmod +x ./AdobeAIRInstaller.bin
chmod: changing permissions of `./AdobeAIRInstaller.bin': Operation not permitted
rayray@ANONYMOUS:~$ sudo chmod +x ./AdobeAIRInstaller.bin
rayray@ANONYMOUS:~$ sudo ./AdobeAIRInstaller.bin
rayray@ANONYMOUS:~$ sudo chown rayray:rayray ./AdobeAIRInstaller.bin
rayray@ANONYMOUS:~$ chmod +x ./AdobeAIRInstaller.bin
rayray@ANONYMOUS:~$ sudo ./AdobeAIRInstaller.bin

```

I never had this problem with Gnome so I dunno what I should do now. After chmoding it and chowning it, it still won't install. I included a screen shot of what it says.

---

### Post by Rayray333 on 2011-05-05
One whole day...

BUMP

---

