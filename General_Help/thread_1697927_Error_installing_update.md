---
title: "Error installing update"
date: 2011-03-01
forum: General Help
---

### Post by texpat on 2011-03-01
During a recent update, a package called "Firmware for Linux kernel drivers" could not be installed, producing an error message that reads:

```
Preparing to replace linux-firmware 1.38.3 (using .../linux-firmware_1.38.4_all.deb) ...
Unpacking replacement linux-firmware ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.38.4_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_1.38.4_all.deb
```

According to the package description its a Wifi-related update. Since my machine doesn't have Wifi, I don't need it, of course, but every time the update manager runs, it'll spring the error into my face.

Any ideas how to get rid of this?

---

### Post by plucky on 2011-03-01
Try from a terminal ```
sudo apt-get clean
sudo apt-get install -f
```

and see if it fixes the problem.

The "sudo apt-get clean" will delete all the downloaded packages in the apt-get archive,so if you want to keep them,don't run the command,but you probably need to delete the file "linux-firmware_1.38.4_all.deb" from the **var/cache/apt/archives** before you run the second command.

Good luck

---

### Post by texpat on 2011-03-02
Cheers plucky!

That did it. Nice one!

---

