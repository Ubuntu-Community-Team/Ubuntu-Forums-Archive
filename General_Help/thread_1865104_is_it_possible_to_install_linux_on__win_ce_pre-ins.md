---
title: "is it possible to install linux on  win ce pre-installed wespro netbook"
date: 2011-10-19
forum: General Help
---

### Post by satheeshkumarvs on 2011-10-19
Recently i got a wespro windows ce pre- insatalled netbook which has only 128 ram 2gb Nand flash

  is it possible to install a linux operating system replacing windows ce 

please answer me it is very important to me because windows ce is not running smoothly and applications become currept.

---

### Post by olain on 2011-10-19
you can try wubi: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by satheeshkumarvs on 2011-10-19
i think the wubi installer did not work within windows ce 

it shows it is not windows ce application

---

### Post by blackbird34 on 2011-10-19
Yes, probably Lubuntu. there's an official version now, Lubuntu 11.10, or else the earlier ones. You coul use LXDE or **Openbox**... but then would it be compatible with the hardware, I don't know, you have to try.  And also find out if you can boot from usb on that netbook, to install...

(Edit: maybe not, then)

---

### Post by olain on 2011-10-19
Try this if you have a usb cd player like a laptop:
Equipment:
1. Cable with usb in both ends.
2. Usb cd player.
Do this:
1. Connect the usb from the laptop to the netbook.
2. Insert the iso burnt cd/dvd into the laptop.
3. Try with the help of the web to install it from there.

Hope this is of help.

---

### Post by dusanyu on 2011-10-19
do you have a model number?

you have a couple of issues to look at 

Issue #0. Processor architecture.  being a Win CE device there is a high probability that this is not a X86 based machine if this is the case you will need a Linux distro that supports that architecture as well as issue #1

Now lets say on the light chance it is X86 you have to deal with issue #1

Issue #1. limited capacity of the machine chance are you will not be shoehorning Ubuntu in that thing anytime soon and would have to look at a extremely light distro. such as [Tiny Core]("http://distro.ibiblio.org/tinycorelinux/welcome.html")

---

### Post by spiky001 on 2011-10-19
With 128 of ram you wil have to look for a light weight distro [http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

---

