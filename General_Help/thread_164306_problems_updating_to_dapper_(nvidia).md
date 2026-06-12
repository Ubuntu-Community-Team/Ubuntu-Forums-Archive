---
title: "problems updating to dapper (nvidia)"
date: 2006-04-22
forum: General Help
---

### Post by chrisv on 2006-04-22
I foolishly tried to update to the beta. Well after dling all the updates I get an X problem and X fails to start 

I checked the X messages and it gives an error saying that the Nvidia modules are not the same version as the X modules and it cannot start up the nvidia kernel. Or something of the sort. 

The problem is that now i cannot get it working even for older kernels. I cannot go back Breezy and have it work. 

Can anyone help?

---

### Post by tonyr on 2006-04-22
Try removing whatever linux-restricted-modules package is installed, and /or installing
the linux-restricted-modules package that matches your kernel (2.6.15-20?)  Some
have had success with this.  There is extensive help at 
[URL="http://www.ubuntuforums.org/showthread.php?t=139264&highlight=nvidia"]
http://www.ubuntuforums.org/showthread.php?t=139264&highlight=nvidia[/URL]

---

### Post by PriceChild on 2006-04-22
Rerun the NVIDIA drivers install script.

---

