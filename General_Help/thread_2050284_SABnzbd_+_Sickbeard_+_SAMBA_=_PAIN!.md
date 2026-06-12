---
title: "SABnzbd + Sickbeard + SAMBA = PAIN!"
date: 2012-08-30
forum: General Help
---

### Post by mizifih on 2012-08-30
Hi there! How are you folks.

Look, reading the title it might sound like I'm having problems with SABnzbd or Sickbeard, but I'm not, they're both working great! 

**The problem is**, they're running on a _Ubuntu Server_ machine and I need to make Sickbeard transfer the files to my _Windows 7_ machine.

I tried lots of commands that I found on the internet to mount the windows shares inside my server, effortless. I mean, it looks like it's working, but it's not.

What I did was include this on my */etc/fstab*
```
//192.168.1.11/tvshow /home/<username>/mount cifs uid=<ubuntu_username>,user=<windows_username>,password=<windows_passwd> 0   0
```

When I reboot the machine it start working, but once Sickbeard start moving stuff around, looks like the connection goes *kaput*. So it's not Sickbeard or SABnzbd that are not working, it's the sharing thing.

I tried lots of mount command but none worked, It's actually starting to **** me off, LOL. I can't believe they couldn't come up with something simple as
```
#samba share /Windows_IP_path/ /Linux_path/ permissions
#samba unshare /Linux_path/
```

Why can't they simplify stuff like that? LOL.

Can someone help me create a persistent sharing between the Windows and Ubuntu Server? Please!? I'm dying of agony and pain in the brains here! LOL!

The windows share is working fine, I can access it from a tablet or the WDTV.

Your help would be much appreciated, thanks ;)

---

