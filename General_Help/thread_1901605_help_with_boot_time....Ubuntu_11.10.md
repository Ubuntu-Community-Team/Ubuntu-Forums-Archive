---
title: "help with boot time....Ubuntu 11.10"
date: 2011-12-28
forum: General Help
---

### Post by KrisDeniseRiley1 on 2011-12-28
So a few months back I was playing around with virtualbox on my laptop with Ubuntu 11.10. I had problems at the time with being able to read usb flash drive with virtualbox so I went online and find a forum spot with some directions on how to get it to work. The problem now is that I don't have virtualbox anymore and I cant remember how or what I modified to get it to work. Now on startup I get a lot of stalling. When I press F11, I see that it keeps saying
[B]"mount: mount point /sus/bus/usb/drivers does not exist"
"mountall: mount /sus/bus/usb/drivers [996] terminated with status"
                             "mountall: Filesystem could not be mounted: /sus/bus/usb/drivers"[/B]

Did I some how mess with a startup file and missed spelled the word "sys" with "sus"?

I expect that my laptop using dhcp for an address is going to take alittle bit of time, but it's a drag for me. If you have any other ideas for better bootup speed let me know please. I really would like to fix the mess that I mentioned above. Please!!!!

---

### Post by 2F4U on 2011-12-29
It looks to me as if you have an entry for usb in /etc/fstab and it is  set to automatically mount at startup. If no usb is present, the system  searches for it and this takes time. I would make a backup of /etc/fstab  and then remove the entry for usb from the original file.

---

