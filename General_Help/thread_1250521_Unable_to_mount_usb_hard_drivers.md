---
title: "Unable to mount usb hard drivers"
date: 2009-08-26
forum: General Help
---

### Post by styler4 on 2009-08-26
I am running Ubuntu 9.04 within Virtualbox. Although, the usb hard drives that I am trying to mount appear in the virtual box under USB devices, neither of the two drives automount or are found with lsusb or sudo fdisk -l. Does anyone have any idea what I am missing? Any help is greatly appreciated.
Scott

---

### Post by Tclarkie on 2009-08-26
how have you plugged them in

---

### Post by styler4 on 2009-08-26
They are both connected directly through the pc's usb ports.

---

### Post by Revolutionary101 on 2009-08-26
There should be an option in settings before you start Ubuntu. Then you should be able to find the usb devices.

---

### Post by P4man on 2009-08-26
the opensource edition doesnt support USB devices. Did you install the OSE version, or the closed source one from Sun's website?

Unless you really need usb support, you can however access the drives through the network. Create a share for them in VB, then in the VM access them by browsing the network. cf the VB documentation.

---

### Post by styler4 on 2009-08-26
I am running the Sun Microsystems version of VirtualBox. Also, USB is enabled under settings, but I am still not able to detect the hard drives.

---

### Post by P4man on 2009-08-26
> **styler4 said:**
> I am running the Sun Microsystems version of VirtualBox. Also, USB is enabled under settings, but I am still not able to detect the hard drives.

Well, all versions of virtualbox are by Sun. And its surprisingly hard to find out if you have the OSE or not. If you installed it through add/remove programs (or synaptic) without manually adding repositories, then you have the OSE version (check in synaptic or add/remove programs which is installed). It may show USB filters, but it won't work.

---

### Post by P4man on 2009-08-26
try this:

```
sudo apt-get remove virtualbox-ose
```

If you have the ose version, you have to remove it anyway before installing the closed source version. If you dont have the OSE, it will tell you its not installed :)

---

### Post by styler4 on 2009-08-26
I got typed "sudo apt-get remove virtualbox-ose", and got the response that the package wasn't found. Any thoughts?

---

### Post by Revolutionary101 on 2009-08-26
> **P4man said:**
> try this:

```
sudo apt-get remove virtualbox-ose
```If you have the ose version, you have to remove it anyway before installing the closed source version. If you dont have the OSE, it will tell you its not installed :)

He said he was running Ubuntu on virtualbox via a different OS.

---

### Post by styler4 on 2009-08-26
Can anyone tell me where I can get a non-open-source version of virtualbox?

---

### Post by P4man on 2009-08-27
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by P4man on 2009-08-27
BTW, can you confirm you are using an virtualized ubuntu on a windows (or mac?) host ?

In that case you probably already have the "Personal Use and Evaluation License (PUEL)" version, not the OSE edition.

Try executing "lsusb" in a terminal to list USB devices

---

### Post by styler4 on 2009-08-27
Thanks for your response. I am running a virtualized Ubuntu on a pc windows machine. The virtualbox that I am having difficulty with is a binary that was  obtained from the link [[COLOR=#000000]http://www.virtualbox.org/wiki/Downloads[/COLOR]]("http://www.virtualbox.org/wiki/Downloads") , that you provided.
 
When I try lsusb, my external usb hard drive is not listed.

---

### Post by P4man on 2009-08-27
ok sorry for misreading your initial post. most posts here about VB and usb are because in ubuntu by default it installs the OSE version without support for USB.

Im not really sure if its needed, but did you install the VB guest additions in VB? Do other USB devices appear in lsusb ? Do you even get a usb root hub?

---

### Post by styler4 on 2009-08-27
I installed the binaries avaliable at [[COLOR=#000000]http://www.virtualbox.org/wiki/Downloads[/COLOR]]("http://www.virtualbox.org/wiki/Downloads"), instead of the OSE download. Is there anything that I needed to do during the installation to make sure that the non-OSE version was installed? No other USB devices appear in lsusb. However I do get a usb root hub.

---

### Post by P4man on 2009-08-27
No, you will have the correct version. Again, i was going by the (wrong) assumption you were installing on an ubuntu host, and in ubuntu you usually install software from the repositories, and the version offered there is the OSE. On windows you go to websites, download exe's and install. You got the right version Im sure.

I got no other idea's, I can only suggest you post your problem on virtualbox forum if you haven't already ..

---

### Post by Tclarkie on 2009-08-27
go into add remove, type ose

---

