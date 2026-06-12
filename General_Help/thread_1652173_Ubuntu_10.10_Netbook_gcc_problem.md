---
title: "Ubuntu 10.10 Netbook gcc problem"
date: 2010-12-24
forum: General Help
---

### Post by Khronos14 on 2010-12-24
Hello, today I have installed Ubuntu 10.10 netbook edition in my Asus Eee Pc 1015PEM. I wanna install the broadcom drivers and I am following a tutorial. The problem appears when I need the gcc to install dkms...

The error:

The program 'gcc' can be found in the following packages:
* gcc
* pentium-builder

I used "sudo apt-get install gcc pentium-builder", but the error doesn´t disappear.

Thanks for answers and sorry for my bad English.

---

### Post by tredegar on 2010-12-24
Try **sudo apt-get install build-essential**

---

### Post by Khronos14 on 2010-12-24
Thanks for the answer, I  have tried that command.

It shows me the next error:

The package <<build-essentail>> has no installation candidate

---

### Post by tredegar on 2010-12-24
Please check your spelling of **build-essential**

---

### Post by Khronos14 on 2010-12-24
It´s right, I wrote "build-essentail" in the post, no in the terminal.

Thanks.

---

### Post by tredegar on 2010-12-24
Well, it should be there, I just  checked that the package exists for 10.10
Maybe you need to do a **sudo apt-get update** first, and then try to get build-essential.

You should see it listed in System - Administration - Synaptic

You do realise that you need an internet connection for this to work?

---

### Post by Khronos14 on 2010-12-24
I am installing the broadcom drivers for wifi and I have no Internet connection in the netbook. I tried to connect a STP with RJ45 but the problem doesn´t disappear, no network :(

Thanks

---

### Post by tredegar on 2010-12-24
You are going to have to get an ethernet connection working with a cable.

Normally, if you plug an ethernet connection into your laptop and router, then boot, a connection will be made at the next boot.

Then you can install / download the software you need and _then_ fix the wireless.

What is a "STP"?

---

