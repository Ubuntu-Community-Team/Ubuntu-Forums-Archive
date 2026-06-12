---
title: "problem with ubuntu 10.10 maverick"
date: 2010-08-19
forum: General Help
---

### Post by ay0ub on 2010-08-19
i upgrande to ubuntu 10.10 maverick 
when i restart it show black screen say : 
Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose
there someone could help me thank you all

---

### Post by Dalek Draco ON LINUX on 2010-08-19
what does it say when you run '/usr/bin/check-bios-nx --verbose'?

It may be that you don't have the necessary kernel version or you're missing an important update?

---

### Post by dcstar on 2010-08-20
> **ay0ub said:**
> i upgrande to ubuntu 10.10 maverick 
.........

Pre-release software is **only** to be discussed in the development forum for that software, because that is the only place where you get any useful help.

Anyone who "upgrades" to a release months before it is officially released should realise that they are using development software.

---

### Post by davrosuk on 2010-08-20
What the OS is looking for is a security feature that is present on most modern CPU's. The operation of the NX bit (No eXecute) feature is set within the BIOS and has to be switched on manually on a lot of boards. Intel refer to the technology as XD, AMD have another name for it.

My advice is go into your BIOS and if the feature is available, turn it on. :-)

---

### Post by ay0ub on 2010-08-22
> **davrosuk said:**
> What the OS is looking for is a security feature that is present on most modern CPU's. The operation of the NX bit (No eXecute) feature is set within the BIOS and has to be switched on manually on a lot of boards. Intel refer to the technology as XD, AMD have another name for it.

My advice is go into your BIOS and if the feature is available, turn it on. :-)
what dvice in bios , how do i change it  ? i'm not very good i upgrade from 10.04 TO 10.10 it drive me crazy

---

### Post by ~Las~ on 2010-08-23
Go through your mother board manual or post it's name /version number

---

### Post by ay0ub on 2010-08-23
mather beard **** 		 		 			SAMSUNG ELECTRONICS CO., LTD. R59P/R60P/R61P 		

thanks all

---

### Post by narcisgarcia on 2010-12-26
I see the "check-bios-nx" message in a lot of computers, and because of lacking BIOS option to enable NX feature, now I remove the warning message:

```
sudo rm /etc/update-motd.d/20-cpu-checker
```

---

