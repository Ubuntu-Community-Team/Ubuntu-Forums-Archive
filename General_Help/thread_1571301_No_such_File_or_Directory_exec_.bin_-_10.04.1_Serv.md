---
title: "No such File or Directory exec .bin - 10.04.1 Server"
date: 2010-09-09
forum: General Help
---

### Post by basalt on 2010-09-09
I just installed 10.04.1 Server 64 bit on a XenServer 5.5 Virtual machine to run JasperServer. I downloaded the .bin file, made it executable. 
 
When I then try to execute the .bin I get an error "bash: ./jasperserver-ce-3.7.0-linux-installer.bin: No such file or directory"
 
Any ideas? The file exists, it IS executable. I already re-downloaded it from a different source. I had installed JasperServer on another machine earlier so this should work.
 
Thanks

---

### Post by basalt on 2010-09-09
Found this: [http://ubuntuforums.org/showthread.php?t=843087&page=2](http://ubuntuforums.org/showthread.php?t=843087&page=2)

Installed 32 bit libs and it works.

---

