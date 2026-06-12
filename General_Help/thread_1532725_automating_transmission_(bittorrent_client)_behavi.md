---
title: "automating transmission (bittorrent client) behavior"
date: 2010-07-16
forum: General Help
---

### Post by robsarm on 2010-07-16
I've searched around and have come up empty. 
I seem to have speed / bandwidth issues running transmission and firefox concurrently. I've played with the speed settings in transmission and my current work around is simply to enable / disable temporary speed settings on transmission when running firefox. i.e. I disable temp speeds when browsing then re-enable when I'm done.

Having failed to find a better solution I am now wondering if there   is a way to automate this process? Is there a script I could run to disable temp speeds when firefox is running then automatically enable them when I close firefox?

---

### Post by lovinglinux on 2010-07-17
You need to limit UPLOAD speed in the torrent client to 80% of your real UPLOAD bandwidth, otherwise it will clog your network and make browsing slow.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

Also make sure you have ipv6 disabled.

Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

---

### Post by robsarm on 2010-07-20
Thanks for your help

---

