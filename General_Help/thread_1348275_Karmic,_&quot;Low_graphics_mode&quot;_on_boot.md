---
title: "Karmic, &quot;Low graphics mode&quot; on boot"
date: 2009-12-07
forum: General Help
---

### Post by aarons6 on 2009-12-07
you have to push the exit to console to get it to go to the login screen.. 
it does it everytime.. doesnt seem to effect anything, just annoying.

any ideas?

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
Do ```
sudo dpkg-reconfigure xserver-xorg
``` before you go into KDE.

---

### Post by Syscraft on 2009-12-07
Thanks for making me aware to this query.. i will definately go through this & find it out the answer for your query.. thanxx :D

---

### Post by aarons6 on 2009-12-07
> **Sin@Sin-Sacrifice said:**
> Do ```
sudo dpkg-reconfigure xserver-xorg
``` before you go into KDE.
 
 
i did this and now it wont boot at all.
it says
 
(EE) XKB: No components provided fo device Virtual core keyboard..
 
confused as i didnt change anything at all.

---

### Post by pchev on 2009-12-07
Take a look at this bug that affect anyone not using gdm but with gdm installed on the system:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483)

As the way to fix this cleanly is still in discussion you can apply this quick fix in the mean time:
add exit 0 at the beginning of the file /etc/gdm/failsafeXServer

---

### Post by aarons6 on 2009-12-07
> **pchev said:**
> Take a look at this bug that affect anyone not using gdm but with gdm installed on the system:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483)

As the way to fix this cleanly is still in discussion you can apply this quick fix in the mean time:
add exit 0 at the beginning of the file /etc/gdm/failsafeXServer

so under bin/bash just put
exit 0

ill try that and get back to you.

---

### Post by aarons6 on 2009-12-07
ok that worked :)

thanks

---

### Post by AtesComp on 2009-12-08
The above bug does seem to be the problem.  The fix is now in karmic proposed updates as a GDM update.[URL="https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483"]
[/URL]

---

