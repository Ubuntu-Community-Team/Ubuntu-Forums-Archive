---
title: "Not able to boot ubuntu 11.10"
date: 2012-06-02
forum: General Help
---

### Post by kira.argunova on 2012-06-02
Hi,
While booting Ubuntu 11.10, the process gets stuck after
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)

Initially it was getting stuck after the login screen appeared and i entered my password at
checking battery state...
after which it would go back to the login screen
I was able to use login as guest and using terminal then...

I purged and installed lightdm... no use

Then I followed instructions on some ubuntu form which said i should use openchrome driver... followed the steps to install and now it gets stuck at

ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)

Please Help!
I need to get this fixed soon!

---

### Post by kira.argunova on 2012-06-02
also i tried to edit the commandline
with i915.modeset=0
and
i915.modeset=1
in both cases it gets stuck after "checking battery state    [OK]"

---

### Post by dino99 on 2012-06-02
often get this "checking battery state" issue due to borked xorg.conf

sudo rm /etc/X11/xorg.conf

then logout & reboot

---

### Post by kira.argunova on 2012-06-02
Thanks for the help :),
But I started the upgrade to 12.04... Will try out if the problem persists, or will let you know if it doesn't.
Thanks again!

---

### Post by kira.argunova on 2012-06-03
Hey,
The upgrade worked out great, 12.04 LTS is awesome :)

---

