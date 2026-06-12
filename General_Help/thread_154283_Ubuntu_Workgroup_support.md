---
title: "Ubuntu Workgroup support"
date: 2006-04-02
forum: General Help
---

### Post by WillisBueller on 2006-04-02
Hello, wondering if anyone has any experience getting ubuntu to integrate with a windows workgroup. 

Here's the setup, I'm in my university's residence, prior to moving to linux i was able to just type //name and pull up a computer. In an attempt to restore that functionality I installed WinBind
[http://www.ubuntuforums.org/showthread.php?t=88206](http://www.ubuntuforums.org/showthread.php?t=88206)
with no luck. I've configured my smb.conf with workgroup set. 

set nsswitch.conf
*hosts:          files wins dns*
[I]
ping //name, ping name[/I]
returns
*ping: unknown host name*
[I]
nmblookup '*'[/I]
returns 
*name_query failed to find name **

also, i've set my server name in my netbios name in smb.conf, but no one can recognize me by my netbios name.

I'm using firestarter as a firewall, but have setup the smb ports.

Any help would be greatly appreciated.

Thanks in advance,
Willis

---

### Post by WillisBueller on 2006-04-04
bump?
I'm beginning to wonder if it has to do with not broadcasting to the correct ports.

---

### Post by Stormbringer on 2006-04-04
[QUOTE=WillisBueller]i've set my server name in my netbios name in smb.conf, but no one can recognize me by my netbios name.
[/QUOTE]

Add "wins support = yes" to the [General] section of your smb.conf. This will enable the Windows Internet Name Service - it's required for hostname lookups if you don't use a local DNS for your lan.

Your nssswitch.conf already contains "wins" in the "hosts:" line, so you don't need to do this modification.

[QUOTE=WillisBueller]
I'm using firestarter as a firewall, but have setup the smb ports.
[/QUOTE]

WINS listens on port 445 - make sure it's accessible through firestarter.

Cheers,
Storm.

---

