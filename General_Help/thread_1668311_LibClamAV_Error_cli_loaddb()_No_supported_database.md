---
title: "LibClamAV Error: cli_loaddb(): No supported database files found in /var/lib/clamav/"
date: 2011-01-16
forum: General Help
---

### Post by crixtiano on 2011-01-16
Hello friends, 

I use 64 bits Ubuntu 10.04.1 LTS (Lucid). 

I try to install and run clamav antivirus, but the software generated an error:

```
# clamscan -r --bell -i /home/cris/Downloads
LibClamAV Error: cli_loaddb(): No supported database files found in /var/lib/clamav/
ERROR: Can't open file or directory


```

So, what does it means? 

Can someone help me with that problem? 

Thank you!

Cristiano M. Magalhaes

---

### Post by jjlee on 2013-02-17
I had the same problem. For me **sudo freshclam** updated the virus definitions and then **clamscan** worked fine.
If this dosn't work for you try [https://wiki.archlinux.org/index.php/ClamAV]("https://wiki.archlinux.org/index.php/ClamAV")

---

