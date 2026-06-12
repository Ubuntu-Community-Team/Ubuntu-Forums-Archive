---
title: "[SOLVED] Belkin UPS F6C550-AVR"
date: 2006-02-11
forum: General Help
---

### Post by sebth on 2006-02-11
I have a Belkin F6C550-AVR usb UPS. I'm trying to use NUT to read the battery level. I installed nut and nut-usb packages. 

In /etc/nut/ups.conf I have 
[belkin]
    driver=newhidups
    port=auto

(I have other files too but I don't think that they make a difference at this point)

When I plug the USB cable, I get this in /var/log/syslog :
[4309459.395000] hiddev96: USB HID v1.11 Device [Belkin UPS] on usb-0000:00:1d.0-1

invoke-rc.d nut start gives me this :
Starting Network UPS Tools: (upsdrvctl failed) upsd upsmon.

I tried starting upsd directly with the upsd command and I got this :
Can't connect to UPS [belkin] (newhidups-auto): No such file or directory

I also noted that when my UPS is plugged in, the file "/dev/usb/hiddev0" exists but it doesn't when I unplug the UPS. 

I tried several times to find informations about this but I found nothing that could help me. Maybe I just didn't search at the right places... I really don't know what I can do now so I ask your help. 

I know you probably need other information about my system, just tell me what you need to know.

Thank you very much

---

