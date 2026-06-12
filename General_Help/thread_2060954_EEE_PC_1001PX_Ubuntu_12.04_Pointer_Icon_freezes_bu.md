---
title: "EEE PC 1001PX Ubuntu 12.04 Pointer Icon freezes but Touchpad Scroll Still Works."
date: 2012-09-21
forum: General Help
---

### Post by djxcon on 2012-09-21
Hi fellow Ubuntu users...I have a bit of a strange thing happening on an ASUS EEEPC (Model 1001px). This happens a few times a week but cannot be replicated on demand. Sometimes (typically when opening a website), the mouse pointer on the screen freezes. When this happens, the edges of the touchpad work, but you cannot move the pointer with the touchpad. So, it's like the touchpad is partially dead. To fix the issue, you can either reboot or you can shut the lid of the netbook to put it to sleep. When you open the lid and wake it up, the pointer is working again. 

Any ideas how to fix this? If not, what is it about the sleep/wake process that fixes it? Is it some kind of module unloading and reloading? Perhaps I can have an even better workaround by creating a script that can be run with ALT + F2 since the keyboard still works. Or I can drop to TTY6 and run a script...just trying to make it so that this is either fixed completely or have a way to restore functionality quickly. 

Any ideas?

---

### Post by HazE_nMe on 2012-10-09
> **djxcon said:**
> Hi fellow Ubuntu users...I have a bit of a strange thing happening on an ASUS EEEPC (Model 1001px). This happens a few times a week but cannot be replicated on demand. Sometimes (typically when opening a website), the mouse pointer on the screen freezes. When this happens, the edges of the touchpad work, but you cannot move the pointer with the touchpad. So, it's like the touchpad is partially dead. To fix the issue, you can either reboot or you can shut the lid of the netbook to put it to sleep. When you open the lid and wake it up, the pointer is working again. 

Any ideas how to fix this? If not, what is it about the sleep/wake process that fixes it? Is it some kind of module unloading and reloading? Perhaps I can have an even better workaround by creating a script that can be run with ALT + F2 since the keyboard still works. Or I can drop to TTY6 and run a script...just trying to make it so that this is either fixed completely or have a way to restore functionality quickly. 

Any ideas?

I also experience this issue on my Dell Studio XPS 1645. I was previously able to open a terminal and kill syndaemon and restart it and all would be well. After a fairly recent update, I no longer have a process called syndaemon and have been just restarting the laptop to get my trackpad to work. BT mouse still works when the trackpad freezes.

When I have 2 finger scrolling enabled, and the trackpad freezes on me, any vertical movement on the trackpad results in scrolling on the focused window. It is still reading input, but is somehow stuck trying to scroll instead of move the pointer.

---

