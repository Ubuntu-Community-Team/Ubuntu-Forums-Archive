---
title: "Unable to run teamviewer7 on 12.04"
date: 2012-09-05
forum: General Help
---

### Post by luvshines on 2012-09-05
teamviewer7 for linux just refuses to run on my 12.04 installation.

segfaults with some error

```

TeamViewer: 7.0.9360
Profile: /home/luvshines (luvshines)
Desktop:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise

        preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
/opt/teamviewer/teamviewer/7/bin/wrapper: line 162: 10907 Segmentation fault      (core dumped) "$WINELOADER" regedit "$TV_script_dir/fontsmooth_rgb.reg"
preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
/opt/teamviewer/teamviewer/7/bin/wrapper: line 162: 10911 Segmentation fault      (core dumped) "$WINELOADER" regedit "$TV_script_dir/no_xvidmodeext.reg"
preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
/opt/teamviewer/teamviewer/7/bin/wrapper: line 162: 10915 Segmentation fault      (core dumped) "$WINELOADER" regedit "$TV_script_dir/no_xrandr.reg"
preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
/opt/teamviewer/teamviewer/7/bin/wrapper: line 162: 10919 Segmentation fault      (core dumped) "$WINELOADER" regedit "$TV_script_dir/no_fileassocs.reg"
preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
/opt/teamviewer/teamviewer/7/bin/wrapper: line 162: 10923 Segmentation fault      (core dumped) "$WINELOADER" regedit "$TV_script_dir/setwinver.reg"
        libXtst.so.6 => /usr/lib/i386-linux-gnu/libXtst.so.6 (0xb75ce000)
preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
/opt/teamviewer/teamviewer/7/bin/wrapper: line 37: 10934 Segmentation fault      (core dumped) "$TV_Wine_bin/$binary" "$@"
```

I don't have wine installed. From what I could read on the net, it's not a requirement for teamviewer for linux, right ?
I was using teamviewer6, without wine, when I was on 10.10

Any ideas ??

---

### Post by luvshines on 2012-09-10
Bump !!

---

### Post by uliandim on 2012-09-10
Try this - [http://www.dimitech.eu/infusions/pro_download_panel/download.php?did=3088](http://www.dimitech.eu/infusions/pro_download_panel/download.php?did=3088)

---

### Post by Jorel on 2012-09-10
Hi,

I just use the Ubuntu Software center for installing Teamviewer and it works perfectly, even gives me the latest update version for Teamviewer.

or you can try these [http://www.ubuntugeek.com/how-to-install-team-viewer-version-7-on-ubuntu-12-04-precise-pangolin.html](http://www.ubuntugeek.com/how-to-install-team-viewer-version-7-on-ubuntu-12-04-precise-pangolin.html)

---

### Post by luvshines on 2012-09-11
> **Jorel said:**
> 
I just use the Ubuntu Software center for installing Teamviewer and it works perfectly, even gives me the latest update version for Teamviewer.

Is it available in the Software center. Mine doesn't show up any
I tried the other method described in the link but no success. Both 6 and 7 version fail with the same error

---

### Post by luvshines on 2012-09-22
Yo Yo !!
Got it working now :guitar:

Fundoo...

This link gave me the hint
[http://www.codeweavers.com/support/tickets/browse/?ticket_id=762859](http://www.codeweavers.com/support/tickets/browse/?ticket_id=762859)

As a part of some crappy security compliance[it's a company issued laptop], the laptop had 'Symantec Antivirus' installed

The error I was observing was due to it blocking wine program

Purged 'symantec antivirus', rebooted the laptop and teamviewer sprang to life

Marking this SOLVED

---

