---
title: "GRUB kernel Options."
date: 2011-03-11
forum: General Help
---

### Post by jailed on 2011-03-11
Hi,

I have Kubuntu 10.10 and Back Track 4 (BT4) Linux installed on my system. I think BT4 is based on Ubuntu 8.10. 

I have the following line for my kernel boot options in *_/etc/default/grub_* file. 

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset [COLOR="Red"]rootdelay=80[/COLOR] quiet splash"

```

I need the *_rootdelay_* option for the _Kubuntu 10.10_ kernel but the BT4 kernel does not need it. But looks like setting this has a global effect and it waits for 80 (seconds ?) even when starting the BT4 kernel which is not required. 

So is there a way to give the rootdelay option only to the Kubuntu 10.10 kernel and not to the BT4 kernel. 

Thank you.

---

### Post by lithopsian on 2011-03-11
Go into /etc/grub.d and start coding :)  Bit of a pain, but you can identify particular kernel entries and specify different options.  Probably 06_custom is the one to change.

---

### Post by jailed on 2011-03-12
> **lithopsian said:**
> Go into /etc/grub.d and start coding :)  Bit of a pain, but you can identify particular kernel entries and specify different options.  Probably 06_custom is the one to change.

lithopsian, Thanks for the reply. I looked the headers, looks like I need to go through the headers individually. I found in readme about the 10_* files that probably needs to be changed for custom settings. I did not know that the kernel options need to be changed in the grub.d directory. Thanks for letting me know.

---

