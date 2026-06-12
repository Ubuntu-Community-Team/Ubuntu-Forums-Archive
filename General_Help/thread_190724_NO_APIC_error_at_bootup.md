---
title: "NO APIC error at bootup"
date: 2006-06-06
forum: General Help
---

### Post by michaeljb2005 on 2006-06-06
For some reason when I boot from grub into the kernel it gives me a some sort of error that requires that I put NO APIC as a kernel option.  Why is this?  Can it be fixed?  If not is it ok to change my options permanently to NO APIC so I don't have to type this every time?  If I do that will it effect my performance?  edit: Kernel panic: IO APIC + timer doesn't work! is part of what I get in the error message.

---

### Post by michaeljb2005 on 2006-06-06
I actually saw a post similar to mine here [http://ubuntuforums.org/showthread.php?t=190626](http://ubuntuforums.org/showthread.php?t=190626).
I do have multiple boot options with windows

---

### Post by honeydew on 2006-06-06
I was also recieving this error with a old laptop I had.. have you gone into grub and looked and seen if the 'linux pci=noapic' is enabled.. and if its not maybe try enabeling it.. just use the grub menu and use that as a special boot peram..

reference:
[http://ubuntuforums.org/showthread.php?t=159170](http://ubuntuforums.org/showthread.php?t=159170)
[http://en.wikipedia.org/wiki/Apic](http://en.wikipedia.org/wiki/Apic)

---

### Post by michaeljb2005 on 2006-06-06
[QUOTE=honeydew]I was also recieving this error with a old laptop I had.. have you gone into grub and looked and seen if the 'linux pci=noapic' is enabled.. and if its not maybe try enabeling it.. just use the grub menu and use that as a special boot peram..

reference:
[http://ubuntuforums.org/showthread.php?t=159170](http://ubuntuforums.org/showthread.php?t=159170)
[http://en.wikipedia.org/wiki/Apic](http://en.wikipedia.org/wiki/Apic)[/QUOTE]

Ah, so this is a multiprocessor thing.  Given that my laptop is not multiprocessor then this is not necessary anyway.  I'll disable APIC in my bootup parameters for grub and life will be perfect again.  Thanks.

edit:  This entire thing was unnecessary.  All this seemed to be caused by booting into windows restarting and then booting back into ubuntu.  Next time I restart after booting back into ubuntu once it's fine again.  So I just need to make sure to add noapic to the kernel options for ubuntu everytime I booted into windows previously.  Thanks.  Just thought I might update everyone on this so they know how it was really resolved.  Add noapic would make it so I would never have to do it manually again, but in case this may have some negative performance issues whatsoever I'm going to leave it alone.

---

