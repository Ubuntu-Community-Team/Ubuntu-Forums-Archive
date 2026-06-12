---
title: "ubuntu installing problem"
date: 2011-09-22
forum: General Help
---

### Post by ceng on 2011-09-22
hi,
I tried to install wubi, i followed WubiGuide. And after installing i selected reboot now.
After reboot i select ubuntu, then "Completing the Ubuntu installation for more installation boot options, press 'ESC' now..." and it counts down to zero. And then anything happens.
ubuntu can't be worked.

how can i solve this problem?
i apologize for my bad English.

---

### Post by ceng on 2011-09-22
i installed ubuntu from wubi.exe. i didn't use usb or dvd.

---

### Post by bcbc on 2011-09-22
What are your computer specs: brand/model, graphics card? Are you installing 11.04?

---

### Post by ceng on 2011-09-22
yes ubuntu 11.04, i have downloaded today.
my computer is asus x61sf280dv, graphics card is NVIDIA GeForce GT 220M.
it is 64 bit but my windows 7 operation system is 32 bit, maybe problem is about it?

---

### Post by bcbc on 2011-09-22
No it's not the 64bits (it doesn't matter what version of windows you are running, just whether you have a 64bit cpu - which you do otherwise wubi wouldn't install it).

When you say nothing happens, is there any hard drive activity? There is some issue with some intel graphics chips that has the backlight off (so it's on and running, you just can't see easily). (I am assuming since your graphics card is an optimus type that you have an onboard intel GPU as well).

The other issue might be similar to this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765230](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765230) but that talks of a long delay and then it boots. I guess it depends how long you waited to see if this is the issue.

What I'd do is press ESC to get more options and try with the acpi workaround just to get it booting. After installation is complete you'll need to[ manually adjust]("http://ubuntuforums.org/showthread.php?t=1613132") the boot options again to boot and then run all updates through the Update Manager.

---

