---
title: "Can't get Wireshark to work"
date: 2010-09-29
forum: General Help
---

### Post by Grafixx01 on 2010-09-29
I installed Ubuntu 10.04 on my ASUS Eee PC 1015 but can't get WireShark to recognize my Atheros card. Any ideas?

I know my Atheros card works because I was on my wireless network at my house last night.

---

### Post by colin.p on 2010-09-29
Go up to "applications", right click and select "edit menus" then down to "internet" then select "wireshark" hit properties and then in the "command" box, type "gksu wireshark".
The reason is, you have to run wireshark as root in order for it to work.

---

### Post by Grafixx01 on 2010-09-30
Ok, I did that but it still doesn't work. It doesn't seem to be recognizing the Atheros card OR the RJ45 adaptor. I searched the forum before and installed using the method described so I thought that it installed all the packages and other stuff needed for drivers, etc. 
 
I thought that way would be easier than unzipping the tar.bz2 file and then trying to figure out if it installed correctly from that method.
 
Any other ideas?

---

