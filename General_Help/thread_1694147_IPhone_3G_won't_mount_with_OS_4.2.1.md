---
title: "IPhone 3G won't mount with OS 4.2.1"
date: 2011-02-23
forum: General Help
---

### Post by dagreen1 on 2011-02-23
Unbuntu doesn't recognize my IPhone 3GS. I get the error message:

"Unable to Mount Don" (no wisecracks please!) "DBus error  org.freedesktop.DBus.Error.NoReply: Message did not receive a reply  (timeout by message bus)"

I tried all 3 USB ports on my laptop with the same results.

My IPhone has a message that says: "Charging not supported with this accessory"

Does anyone have a fix for this?

Thanks!

Don

p.s. I'm new to Linux and not well versed on the OS

---

### Post by An Sanct on 2011-02-24
Welcome to the forum!

The message is "Unable to Mount $Device_name$", so device name is whatever you choose to name it.

It is possible to use your iPhone with Ubuntu, you just need to install some additional packages. In short, you need to launch Synaptic and ind this package "libimobiledevice"

Go to System > Administration > Synaptic Package Manager, top left is a quick search edit, insert "libimobiledevice" and make sure, it is installed.

This information is from here ([Using iPhone or iPod on Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPhone")), it would also be best if you read that resource through.

---

