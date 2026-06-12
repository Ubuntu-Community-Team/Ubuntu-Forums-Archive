---
title: "Ubuntu is running in old classic theme. What should i do to run unity ?"
date: 2011-10-13
forum: General Help
---

### Post by vikash_chandola on 2011-10-13
Windows 7 ultimate runs with all of it's graphic effects but Ubuntu is not  running with unity, it runs in fall back mode(with classic looks). What  should i do to run unity.

---

### Post by peter d on 2011-10-13
You probably need to use the proprietary drivers. Alternatively, upgrade to 11.10 which will fall back to Unity 2D instead of Gnome 2.

---

### Post by effenberg0x0 on 2011-10-13
Make sure your PC drivers can't already use it.

```
/usr/lib/nux/unity_support_test -p

```

Find out what VGA you have:
```
lspci | grep -i VGA
```

Read and learn how to setup the best video drivers for it:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Regards,
Effenberg

---

### Post by vikash_chandola on 2011-10-13
> **effenberg0x0 said:**
> Make sure your PC drivers can't already use it.

```
/usr/lib/nux/unity_support_test -p

```Find out what VGA you have:
```
lspci | grep -i VGA
```Read and learn how to setup the best video drivers for it:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Regards,
Effenberg
it's little old Intel Pentium 4; 2.7GHz.
see attachment. There is result of your commands.
Is my computer powerful enough to run unity?
see these images also. these are from windows dxdiag.
[http://ubuntuforums.org/attachment.php?attachmentid=204182&d=1318531585](http://ubuntuforums.org/attachment.php?attachmentid=204182&d=1318531585)
[http://ubuntuforums.org/attachment.php?attachmentid=204181&d=1318531585](http://ubuntuforums.org/attachment.php?attachmentid=204181&d=1318531585)

---

### Post by crdlb on 2011-10-14
Your hardware acceleration is broken. Please attach your /var/log/Xorg.0.log

An intel 945 should certainly be able to run compiz, but the performance may not be excellent.

---

### Post by vikash_chandola on 2011-10-14
> **crdlb said:**
> Your hardware acceleration is broken. Please attach your /var/log/Xorg.0.log

An intel 945 should certainly be able to run compiz, but the performance may not be excellent.
that is it.
friend if it contain any sensitive personal information then please warn me i will remove it

---

### Post by collisionystm on 2011-10-14
All official Intel drivers are included in the Linux Kernel. Your card is just old. Is this a laptop or desktop? If its a desktop just get a new card. If its a laptop... well.... you can always try xfce?

---

### Post by alreadytaken4536 on 2011-10-14
> **effenberg0x0 said:**
> Make sure your PC drivers can't already use it.

```
/usr/lib/nux/unity_support_test -p

```

Regards,
Effenberg

```
~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  22
  Current serial number in output stream:  22

```

Excuse me.. wat?

---

### Post by vikash_chandola on 2011-10-14
> **collisionystm said:**
> All official Intel drivers are included in the Linux Kernel. Your card is just old. Is this a laptop or desktop? If its a desktop just get a new card. If its a laptop... well.... you can always try xfce?
thanks **collisionystm**.It is desktop.I was also thinking so.
I will continue with these old looks. I am thinking to buy a new in July 2012.Till then continue with this computer.But can you tell why windows is running fine even that's system requirement is much greater than windows. Is it just a chance.:confused:
**alreadytaken4536**; I don't understand what you are trying to explain can you please explain again.

---

### Post by crdlb on 2011-10-14
> **vikash_chandola said:**
> that is it.
friend if it contain any sensitive personal information then please warn me i will remove it

The /var/log/Xorg.0.log shouldn't have anything personal.

---

### Post by vikash_chandola on 2011-10-14
> **crdlb said:**
> The /var/log/Xorg.0.log shouldn't have anything personal.
I think uploading files with .log extension is not allowed that's why it was not uploaded in [#6]("http://ubuntuforums.org/showpost.php?p=11341481&postcount=6") post. So see two log files in this .tar.gz file

does installing  [this](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=9722&lang=eng) driver will help.

---

### Post by crdlb on 2011-10-14
You're using the generic VESA driver. That has probably been set in /etc/X11/xorg.conf . You shouldn't need an xorg.conf at all, so try ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.vesa-save
``` Reboot and see if it works.

---

### Post by vikash_chandola on 2011-10-14
> **crdlb said:**
> You're using the generic VESA driver. That has probably been set in /etc/X11/xorg.conf . You shouldn't need an xorg.conf at all, so try ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.vesa-save
``` Reboot and see if it works.
No such file in directory.
see screenshot

---

### Post by crdlb on 2011-10-15
There seems to be something wrong with the intel driver. You could take a look at dmesg, specifically ```
grep intel /var/log/dmesg
```

I found a [similar bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/805700") for Natty, but it is unresolved.

---

### Post by vikash_chandola on 2011-10-15
> **crdlb said:**
> There seems to be something wrong with the intel driver. You could take a look at dmesg, specifically ```
grep intel /var/log/dmesg
```I found a [similar bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/805700") for Natty, but it is unresolved.
yes; about ten months ago i tried to install Ubuntu 10.10 and Linux mint 10 both does not run in GUI runs only in command mode.However at the time of installation Ubuntu was in full GUI(after installation it run in terminal ).
There is something wrong with my graphic driver.

---

