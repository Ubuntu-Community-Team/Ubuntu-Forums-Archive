---
title: "Adding a list to BlockControl"
date: 2011-02-01
forum: General Help
---

### Post by Ankhwatcher on 2011-02-01
Hi,

I'm trying to add this list of [IP Addresses]("http://list.iblocklist.com/?list=steam") to my BlockControl Whitelist.

So far I have been adding the ranges one at a time through the Mobloquer interface, but I have seen IP Addresses which are within these ranges coming up as blocked outputs.

What is the best way to add this list?

Also:
Is there a conflict created if I whitelist and IP and then whitelist and range that includes that IP?

Thanks,
ANkh

---

### Post by jre on 2011-04-25
Just saw your post, if you still need to know:

> **Ankhwatcher said:**
> I'm trying to add this list of [IP Addresses]("http://list.iblocklist.com/?list=steam") to my BlockControl Whitelist.

So far I have been adding the ranges one at a time through the Mobloquer interface, but I have seen IP Addresses which are within these ranges coming up as blocked outputs.

What is the best way to add this list?Download and unpack it to e.g. /etc/blockcontrol/steam
Then set in /etc/blockcontrol/blockcontrol.conf
```
ALLOW_IN="/etc/blockcontrol/steam"
ALLOW_OUT="/etc/blockcontrol/steam"
```

This is just an example, you may freely choose any path and filename on your system.

> **Ankhwatcher said:**
> Also:
Is there a conflict created if I whitelist and IP and then whitelist and range that includes that IP?
No, there's no conflict.

BTW, in the long run, I will add better support for allow lists in pgl, which is just getting its GUI finally :-)

---

### Post by Ankhwatcher on 2011-04-25
> **jre said:**
> Just saw your post, if you still need to know:

Download and unpack it to e.g. /etc/blockcontrol/steam
Then set in /etc/blockcontrol/blockcontrol.conf
```
ALLOW_IN="/etc/blockcontrol/steam"
ALLOW_OUT="/etc/blockcontrol/steam"
```

This is just an example, you may freely choose any path and filename on your system.


No, there's no conflict.

BTW, in the long run, I will add better support for allow lists in pgl, which is just getting its GUI finally :-)

Thanks!

I managed to get it whitelisted enough to work by throwing IP addresses in a few different ways.

Unfortunately I can't get steam to work on WINE.

I'll need to reinstall my server to get it working and I'm not willing to do that right now. (So much configuration...)

-ANkh

---

### Post by jre on 2011-04-25
If your problems relate to moblock/blockcontrol whitelisting under wine: AFAIK wine requires use of the FORWARD chain (instead of the above mentioned INput and OUTput).

If it relates to steam and wine itself: according to [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163) your chances are good, it's rated platinum.

---

### Post by Ankhwatcher on 2011-04-25
> **jre said:**
> If your problems relate to moblock/blockcontrol whitelisting under wine: AFAIK wine requires use of the FORWARD chain (instead of the above mentioned INput and OUTput).

If it relates to steam and wine itself: according to [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163) your chances are good, it's rated platinum.

I know it is, I'm not giving up for want of trying. It just won't bloody work.
I've sunk days into it and just don't care anymore.

---

