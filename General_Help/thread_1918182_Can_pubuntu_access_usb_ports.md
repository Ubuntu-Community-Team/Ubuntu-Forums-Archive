---
title: "Can pubuntu access usb ports?"
date: 2012-01-31
forum: General Help
---

### Post by lv8402 on 2012-01-31
[ubuntu] Can pubuntu access usb ports?
I've been searching for a long time.
Thanks for help.

---

### Post by seawolf167 on 2012-01-31
I'm not familiar with PUbuntu, but what about using [cygwin]("http://www.cygwin.com/"), a [Wubi install]("http://www.ubuntu.com/download/ubuntu/windows-installer"), or install to a flash drive and run from that with something like [unetbootin]("http://unetbootin.sourceforge.net/")?

---

### Post by lv8402 on 2012-02-01
But I am not allowed to boot from other devices at my school.

---

### Post by 3rdalbum on 2012-02-01
> **lv8402 said:**
> But I am not allowed to boot from other devices at my school.

I've got the feeling that they probably wouldn't like you using Portable Ubuntu on their computers either.

Portable Ubuntu (PUbuntu) uses a virtual machine. It probably doesn't access USB devices directly (it depends if it's using open-source Virtualbox, or the proprietary one, or something else). However if you're talking about accessing a USB flash drive then you should be able to tell the virtual machine software to create a "shared folder" on the USB that both operating systems can access.

If you're talking about accessing USB keyboard and mouse, then these things are already virtualised and will work out-of-the-box.

---

