---
title: "Denied subscription request in Empathy are not preserved."
date: 2010-06-20
forum: General Help
---

### Post by ToshibaLaptoplinux on 2010-06-20
Empathy prompts to approve a subscription request.

I select "No" to deny the request.

If I reboot or logoff of machine upon re-boot the same subscription requests appear.

It is re-producible and happens every time. If I don't reboot or logoff the subscription request will no longer appear. Any ideas?

---

### Post by tigerhawkvok on 2010-08-16
I too experience this -- making it really annoying when spammers try to add you, as you can't actually reject them and have it stick!

---

### Post by ToshibaLaptoplinux on 2010-10-15
This is still a problem in Maverick. Clearly not a critical bug but none-the-less VERY annoying.

---

### Post by proteusmoteus on 2010-12-02
found fix here [http://ubuntuforums.org/showthread.php?t=1509005](http://ubuntuforums.org/showthread.php?t=1509005)

> **sgornick said:**
> This is a reported bug in the telepathy-haze package, see bug #480605

[https://bugs.launchpad.net/ubuntu/+source/telepathy-haze/+bug/480605](https://bugs.launchpad.net/ubuntu/+source/telepathy-haze/+bug/480605)

I was able to get request to go away by accepting the request and then  from the list of authorized contacts, remove the unwanted contact.

Another method is to deny the friend request using Yahoo's webmessenger interface:        [http://webmessenger.yahoo.com]("http://webmessenger.yahoo.com/")

---

