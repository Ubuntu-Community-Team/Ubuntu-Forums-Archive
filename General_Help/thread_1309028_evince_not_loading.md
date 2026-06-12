---
title: "evince not loading"
date: 2009-11-01
forum: General Help
---

### Post by floydwilde on 2009-11-01
After upgrading to karmic, when I try to open pdf documents with evince, it just opens up a window with "document viewer" at the top, and the program never seems to load.   

Just as a quick fix, I tried doing "apt-get remove evince" and then "apt-get install evince" and the same thing happens.  

Anyone else have a similar experience? 

Attached a screen shot.

---

### Post by beaufils on 2009-11-01
I got almost the same trouble: evince is starting but display nothing. It seems that font can not be used (see attached picture).

I fixed it by stopping apparmor:

```
sudo /etc/init.d/apparmor stop
```

I will file a bug and post its reference here as soon as it is done.

---

### Post by beaufils on 2009-11-01
Filed as bug [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/469089](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/469089).

---

### Post by RahulBatra on 2009-11-01
Thanks beaufils.

Meanwhile, here's a temporary fix:
```
sudo mv /etc/apparmor.d/usr.bin.evince ~/
sudo /etc/init.d/apparmor restart
```

---

### Post by beaufils on 2009-11-01
The bug I filed is a duplicate of [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/447292](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/447292). AppArmor user experience is yet to be ameliorated.

In my case the problems comes from AppArmor configuration and the fact that my homedir is a link to another directory. As specified in [https://wiki.ubuntu.com/DebuggingApparmor#Adjusting%20Tunables](https://wiki.ubuntu.com/DebuggingApparmor#Adjusting%20Tunables) I was able to fix it by modifying /etc/apparmor.d/tunables/home.

Hope it helps.

---

### Post by floydwilde on 2009-11-01
ahh, my solution was: 

~# apt-get remove apparmor

Now evince is working again.  Thanks for the tips.

---

### Post by mterlouw on 2009-12-11
> **floydwilde said:**
> ahh, my solution was: 

~# apt-get remove apparmor

Now evince is working again.  Thanks for the tips.If there ever was a case for usable security, this is it.

---

### Post by temuraru on 2010-05-11
I had the same problem with firefox 3.6.3 (not that the version matters...).

I tried some *simple* things: 
[LIST]
[*]I ran firefox as normal user (**firefox** in the console) ->  it happened as described in this forum (no text, and the console was full of errors like: "*_Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc'_*").
[*]I ran firefox as root (**sudo firefox** from the console) -> everything was OK (the console was clean).
[/LIST]

So, the most simple solution was to delete all the fonts (as root):
**cd /usr/share/fonts/truetype/msttcorefonts**
**rm -rf ***
and reinstall them (as normal user):
**sudo apt-get install msttcorefonts**
here i ran into another smaller problem with a ttf font installer, so I had to do: 
*sudo apt-get remove ttf-mscorefonts-installer*
*sudo apt-get install msttcorefonts*

---

### Post by nroussi on 2010-10-15
I have been have this problem after an upgrade to 10.04 from hardy. All my users were having issues with firefox and evince. This was my tail -f /var/log/messages

```
Oct 15 12:49:21 edubuntuS2 kernel: [323744.313428] type=1503 audit(1287161361.288:1883):  operation="open" pid=10597 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=2472 ouid=2472 name="/ldaphomes/nnnn/nnnnn/.Xauthority"
Oct 15 12:49:42 edubuntuS2 kernel: [323765.654301] type=1503 audit(1287161382.628:1884):  operation="open" pid=10615 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=2472 ouid=2472 name="/ldaphomes/nnnn/nnnnn/.ICEauthority"

```

In the name of security as mterlouw suggests, instead of removing apparmor completely, I would run
```
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.evince
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox

```

But all users would get frustrated and tell me, my windows machine at home opens PDFs just fine and Firefox works with not issues. Therefore, I formatted everything, re-installed a fresh copy of the OS but it would still do it. I am guessing that there was some issue with the conf files of the users. I removed all conf files and still. So in the interest of usability over security if removing a buggy and not well tested package like apparmor, then so be it. SELinux needed a cousin I guess...

Thanks to floydwilde for suggesting to remove it.

---

