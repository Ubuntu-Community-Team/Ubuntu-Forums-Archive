---
title: "transmission webinterface"
date: 2010-03-07
forum: General Help
---

### Post by asai on 2010-03-07
I am running transmission daemon 1.22 web-interface on a server.
It runs perfect, but there is a small issue:
If I download files that are larger than 2GB then the status bar shows 100% when it comes to 2GB, but it continues to download.

I found a file called inc-common.php which contains this:
```
<?php
function formatSize($size) {
   $unit = "O";
   if($size/1024 > 1) {
      $size /= 1024;
      $unit = "Ko";
   }

   if($size/1024 > 1) {
      $size /= 1024;
      $unit = "Mo";
   }

   if($size/1024 > 1) {
      $size /= 1024;
      $unit = "Go";
   }

   return sprintf("%.1f %s", $size, $unit);
}

?>
```
Someone who knows if this has nothing to do with it?
What can I possibly change on this file?

---

### Post by asai on 2010-03-08
*bump*

---

### Post by Charles Kerr on 2010-03-08
Transmission's web abilities were rewritten from scratch for 1.30, and the web client was folded into Transmission s.t. you don't have to install Clutch separately.

You might consider upgrading from 1.22 to 1.91.

---

### Post by alecz20 on 2010-08-23
> **Charles Kerr said:**
> 

You might consider upgrading from 1.22 to 1.91.

How do you make this upgrade?

I am running 9.04, and the current version is:
```

~$ transmission-daemon -V
Transmission 1.51 (7963)

```

---

