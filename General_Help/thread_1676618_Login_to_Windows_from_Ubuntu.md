---
title: "Login to Windows from Ubuntu"
date: 2011-01-27
forum: General Help
---

### Post by mac4rfree on 2011-01-27
Hi Guys,

I am having dual boot between windows and ubuntu..

I know we can login as diff user using Xserver when one server is already logged in.

Now, is it possible to login to Windows without restarting the laptop?????

Thanks for your help in advance..

---

### Post by yetiman64 on 2011-01-27
> **mac4rfree said:**
> ...Now, is it possible to login to Windows without restarting the laptop?????...

It is possible to access the NTFS filesystem of Windows as Ubuntu has the ntfs3g filesystem driver.

It is not possible to login to Windows (as an active OS) while Ubuntu is running with a dual boot setup. When one is working the other is dormant. You need to reboot each time to get to the grub bootloader.

The only way I know to login to a Windows OS from Ubuntu (both running together at the same time) is by using a Virtualization program. Virtualbox is one that can be installed from the repositorys (or downloaded directly from the Oracle website).

---

### Post by dhysk on 2011-01-27
I did something like this before I ended up competly switching to Linux myself.  It was a few years ago and you may have to do some searching for a howto, but what I did was use VMware Server to boot my actual windows partition.  3D games didn't work obvoisly threw a virtual machine but what this did was allow me to use my actuall windows install instead of installing a brand new OS in a virtual machine.

Things to consider are:

1. Windows will complain about a change in hardware so you'll have to re-validate Windows. When booting in a VM you will want to use VMwares drivers but when you boot normally you want to use normal drivers in windows.  This was allowed in XP using driver profiles but newer versions of windows I don't think support this option.

2.  If you have an OEM winodws ie runing a Dell, HP, Linvo, ect.. I can't garantee it will work since you can't transfer them over to different hardware (witch a vm basically will be).

3.  Unless you really need a persistant windows environment it's probably just easier to us a virtual machine (VMware or Virtual Box) and do a fresh windows install.

What I do now is run a seperate Windows XP in Virtual Box and when I want to play a game(iRacing) I restart into a Windows XP install on my hard drive.

So yes it's possibl and thiere are a few ways to do this but it depends on your needs.

---

### Post by mac4rfree on 2011-01-28
Exactly i am booting to Windows to play games only.. I love my NFS games.. but i see that virtualization will lag for these games especially for carbon.. 
So, i think i jus need to reboot ....
anywy thanks for the information...

---

### Post by HermanAB on 2011-01-28
Yup, Windows is primarily a game OS.

---

