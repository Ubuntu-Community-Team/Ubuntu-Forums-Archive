---
title: "Can't get netbeans working"
date: 2010-06-13
forum: General Help
---

### Post by Ryzol on 2010-06-13
I'm using Ubuntu 9.04 on a netbook with the remix UI. I downloaded netbeans and orginally it would show a gray screen after the splash screen disappeared. I was able to fix that by adding "export AWT_TOOLKIT=MToolkit" to /etc/profile.

I then disabled a plugin, can't remember which one, and added a plugin to netbeans internal repository. Now netbeans won't start at all. It freezes at the splash screen. I have done a complete removal and a reinstallation, so I doubt the plugin stuff is affecting it.

When I run netbeans from console it hangs, and displays not output until I send it an interrupt. Then it spits out this error message:
> ** (<unknown>:5182): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed

** (<unknown>:5182): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed

** (<unknown>:5182): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed

** (<unknown>:5182): WARNING **: FIXME: wait for completion unimplemented

** (<unknown>:5182): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed

---

### Post by Ryzol on 2010-06-14
Bump. Any ideas? I'm pretty lost here.

---

### Post by bulleye7 on 2010-09-01
I'm having the same issue here.
I'm using Ubuntu Netbook 10.04 and after netbeans splash screen I get a gray window. Looks fine after unmaximizing the window. If I maximize it, it would look gray again.

---

### Post by bulleye7 on 2010-09-01
Found a workaround:
[https://bugs.launchpad.net/ubuntu/+source/maximus/+bug/336064](https://bugs.launchpad.net/ubuntu/+source/maximus/+bug/336064)

So far, it works good.

---

