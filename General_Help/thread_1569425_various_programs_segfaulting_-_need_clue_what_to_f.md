---
title: "various programs segfaulting - need clue what to fix"
date: 2010-09-06
forum: General Help
---

### Post by Tweak42 on 2010-09-06
Need input. My 10.4 install started segfaulting various programs after going through airport TSA inspection.  I haven't found any clues googling and searching forums the last week.  System boots up and logs in to GUI normally.  Only certain programs that auto launch (ex: network manager applet) and some manual launch like synaptic fail to launch and generate the attached errors.  Firefox, and Open Office work fine.  Since the NetworkManager segfaults, I must manually run command lines to connect to wired network.  I probably could get wireless if I figure out the wpa_supplicant commands.

I don't think it's hardware problem since everything that does run is stable, and my windows XP partition is stable.  I've run fsck and manually run apt-get update to no effect.

Any suggestions what to rollback, reinstall or patch?  I aware I could just backup/wipe/reload but prefer to learn how to fix this.

> Sep  6 14:43:34 Wall-e kernel: [   59.168784] nm-applet[1820]: segfault at 0 ip 00007ffc73336e80 sp 00007fffdc82fc18 error 6 in libgtk-x11-2.0.so.0.2000.1[7ffc7323a000+415000]
Sep  6 14:44:05 Wall-e kernel: [   89.719585] evolution-alarm[2007]: segfault at 0 ip 00007f24e6446e80 sp 00007fffcbb4b3b8 error 6 in libgtk-x11-2.0.so.0.2000.1[7f24e634a000+415000]
Sep  6 14:44:05 Wall-e kernel: [   89.796130] python[2005]: segfault at 2137d10 ip 0000000002137d10 sp 00007fff6a71bac8 error 15
Sep  6 14:44:16 Wall-e kernel: [  100.497206] update-manager[2026]: segfault at 1f8c180 ip 0000000001f8c180 sp 00007fffd62f7bc8 error 15
Sep  6 14:44:50 Wall-e kernel: [  135.188668] software-proper[2148]: segfault at 2386ca0 ip 0000000002386ca0 sp 00007fffd0b11728 error 15
Sep  6 14:59:37 Wall-e kernel: [ 1022.351259] totem[2365]: segfault at 1bbb010 ip 0000000001bbb010 sp 00007fff8995d128 error 15


---

### Post by Tweak42 on 2010-10-01
Follow up: Ended up diving in and upgrading to maverick 10.10 using command line since none of the gui tools worked. Fixed everything.

---

