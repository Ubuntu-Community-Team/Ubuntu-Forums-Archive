---
title: "MD5 checksum error for googleearth?"
date: 2010-08-15
forum: General Help
---

### Post by blackdalek on 2010-08-15
I downloaded the GoogleEarthLinux.bin file twice from google.com thinking it might have been a case of corrupted download, but I still get the same error -

$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity...Error in MD5 checksums: 23a82662ebe98d12f2bb0f9a9c9de3ac is different from c82b570db6dfc519d065b8b1a3b69511

Anyone else getting this?

---

### Post by realzippy on 2010-08-15
why not installing googleearth by adding [medibuntu]("http://www.medibuntu.org/index.php") to the sources?

---

### Post by howefield on 2010-08-15
Try another method, there are a couple on this link, one using Medibuntu and the other using googleearth-package to make a deb which you can then install.

[http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/](http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/)

---

### Post by adam_himself on 2010-08-15
> **blackdalek said:**
> I downloaded the GoogleEarthLinux.bin file twice from google.com thinking it might have been a case of corrupted download, but I still get the same error -

$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity...Error in MD5 checksums: 23a82662ebe98d12f2bb0f9a9c9de3ac is different from c82b570db6dfc519d065b8b1a3b69511

Anyone else getting this?

Yes, I was just trying to install Google Earth myself and was getting MD5 checksum errors as well.

realzippy has it right.  Medibuntu solved this.  Just follow their how to add repository then type

```
sudo apt-get install googleearth
```

Works for me now :P

---

