---
title: "NetworkManager Always Reports 100% Signal"
date: 2006-03-05
forum: General Help
---

### Post by OPaul on 2006-03-05
I know this isn't really an Ubuntu related question, but I'm not sure who developers NetworkManager.

No matter what wireless connection I connect to, and no matter how far away from it I am, I always have a 100% connection.

---

### Post by Corvillus on 2006-03-05
Are you using ndiswrapper? If so, it's an ndiswrapper issue...many wireless network management applications will display signal strength as 100% all the time if you use the ndiswrapper driver. The only one I can think of that doesn't do this is wifi-radar.

---

### Post by OPaul on 2006-03-06
I didn't think I was, how do I tell?

---

### Post by OPaul on 2006-03-06
OK, never mind. I am using ndiswrapper. Will a newer version of ndiswrapper correct this, or is just a limitation when using the Windows drivers?

---

### Post by Corvillus on 2006-03-07
I'm not really sure if a new version will correct this or not, but at the moment it's a limitation. Although, wifi-radar does display signal strength for me, so it might just be a limitation of certain APIs or something.

---

