---
title: "Anyone successful setting up WPA2 with rt2500?"
date: 2006-02-19
forum: General Help
---

### Post by jcl on 2006-02-19
Howdy,

I've seen a number of posts about setting up wireless with rt2500(linksys) in /etc/network/interfaces. I cannot seem to get it to work and I'm wondering if it's because I'm setting my router (wrt54g) to WPA2 (TKIP+AES). The only documentation for this line:

pre-up iwpriv ra0 set EncrypType=AES

I see shows either AES *or* TKIP... does it not support TKIP+AES?

Has anyone successfully set up true WPA2 with the rt2500 chipset in linux (and not WPA in compatability mode)?

Thanks

---

### Post by jcl on 2006-02-21
up

---

### Post by jcl on 2006-02-25
up

---

### Post by jcl on 2006-03-02
How about if I ask it this way:

Anyone out there running WPA2 successfully? 

If so would you be kind enough to post your /etc/networks/interfaces? Also what commands can you run to verify that you are actually in WPA2 mode and not WPA compatibility mode?

Thanks

---

### Post by covana on 2006-05-18
bump

---

### Post by wieman01 on 2006-06-25
Hi, 

Want to try this out? I installed Linksys "wusb54g v4" sucessfully using ndiswrapper & WPA2. Perhaps this is helpful.

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

He

---

