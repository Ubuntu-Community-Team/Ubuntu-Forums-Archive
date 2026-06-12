---
title: "How to switch Virtual Box Display from 16 to 32bit"
date: 2011-08-24
forum: General Help
---

### Post by stamatiou on 2011-08-24
Hey guys,
I am trying to install Ubuntu 11.10 Alpha 2 on a Virtual Box but I when I boot it tells me:
>   p, li { white-space: pre-wrap; }  The Virtual Machine reports that the guest OS supports mouse pointer integration. This means that you do not need to *capture* the mouse pointer to be able to use it in your guest OS -- all mouse actions you perform when the mouse pointer is over the Virtual Machine's display are directly sent to the guest OS. If the mouse is currently captured, it will be automatically uncaptured.
 The mouse icon on the status bar will look like  to inform you that mouse pointer integration is supported by the guest OS and is currently turned on.
 Note: Some applications may behave incorrectly in mouse pointer integration mode. You can always disable it for the current session (and enable it again) by selecting the corresponding action from the menu bar.

How can I fix that?

---

### Post by e79 on 2011-08-24
Title is misleading !

But as for the message in your quote, nothing on your end to do except selecting 'do not shot me this message again' !

It basically only tells you that the mouse focus will be captured by the virtual machine whenever you hover it.

---

### Post by stamatiou on 2011-08-25
> **e79 said:**
> Title is misleading !

But as for the message in your quote, nothing on your end to do except selecting 'do not shot me this message again' !

It basically only tells you that the mouse focus will be captured by the virtual machine whenever you hover it.
Oh I'm sorry! :oops:
The message is:
>   p, li { white-space: pre-wrap; }  The virtual machine window is optimized to work in 32 bit color mode but the virtual display is currently set to 16 bit.
 Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
 Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color mode to see if this message disappears or you can simply disable the message now if you are sure the required color mode (32 bit) is not available in the guest OS.
Is there a way to fix that?

---

### Post by e79 on 2011-08-25
Have you installed the 'Guest Addition' on your guest machine ? I had the same message once and it went away after installing it .

---

### Post by stamatiou on 2011-08-25
> **e79 said:**
> Have you installed the 'Guest Addition' on your guest machine ? I had the same message once and it went away after installing it .
What is a Guest Addition?

---

### Post by IT Support on 2011-08-25
> **stamatiou said:**
> What is a Guest Addition?
[img]http://www.wluopensource.org/media/pub/articles/installing-linux-mint-virtualbox-virtual-machine/virtualbox-install-guest-additions.png[/img]

---

### Post by stamatiou on 2011-08-25
> **IT Support said:**
> [IMG]http://www.wluopensource.org/media/pub/articles/installing-linux-mint-virtualbox-virtual-machine/virtualbox-install-guest-additions.png[/IMG]
I click on the option but nothing happens :confused:

---

### Post by e79 on 2011-08-25
Have you downloaded and installed the Guest Addition package on your host first ? Once its installed you can redo the previous operation.

[http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack)

---

### Post by hippiehacker on 2012-01-02
From this post ->[https://forums.virtualbox.org/viewtopic.php?f=2&t=24273](https://forums.virtualbox.org/viewtopic.php?f=2&t=24273) it looks like you can make the warnings go away by settings some extra data params on the command line.

```
VBoxManage setextradata global GUI/SuppressMessages remindAboutAutoCapture,\
confirmInputCapture,remindAboutMouseIntegrationOn,remindAboutWrongColorDepth,\
confirmGoingFullscreen,remindAboutMouseIntegrationOff
```

---

