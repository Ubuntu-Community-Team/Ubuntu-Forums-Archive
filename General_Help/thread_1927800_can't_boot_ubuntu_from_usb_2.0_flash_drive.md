---
title: "can't boot ubuntu from usb 2.0 flash drive"
date: 2012-02-18
forum: General Help
---

### Post by improvent363 on 2012-02-18
I can boot with ubuntu live cd only if I press F6 and select "Nomodeset"  option.

Hence, I need to do the same thing with the flash drive, but when I press f6, I get no option of selecting "nomodeset" or any other option. Therefore, how do I select and enable "nomodeset" on the usb 2.0 flash drive?

---

### Post by winh8r on 2012-02-18
I have not tried this on a USB Flash Drive myself, but you should be able to hold down the shift key as the OS boots and getto a grub menu from there and enter the nomodeset option , instructions will be at bottom of menu box I believe.

If this is incorrect then I apologise in advance.

---

### Post by improvent363 on 2012-02-29
> **winh8r said:**
> I have not tried this on a USB Flash Drive myself, but you should be able to hold down the shift key as the OS boots and getto a grub menu from there and enter the nomodeset option , instructions will be at bottom of menu box I believe.

If this is incorrect then I apologise in advance.

Well, I was able to type "nomodeset" but when I do that, I get this error message: 
"could not find error image: nomodeset".

So, someone please inform me what should I try next?

---

### Post by imachavel on 2012-02-29
Strange, I can see my flash drive, I have Linux mint installed to it, I installed it through windows using an application I found on the net. I can see folders for boot sector and grub, can't boot to the flash drive though. Don't know why. Could just be old mobo, as no error comes up, the bios just hangs when I select flash drive as boot device. Oh well

---

### Post by Gremlinzzz on 2012-02-29
burn ISO using unetbootin use live CD to download ISO and install unetbootin on live cd  use unetbootin to burn iso on usb:popcorn:

---

### Post by imachavel on 2012-02-29
:popcorn: you seem to have xperience.

But it's as though you didn't read the thread. We both have working flash drives, in fact I can put files on mine(which is strange because the drive is partitioned, flash memory partition wonder how the contiguous area works) and OS boot sector and grub are there. Maybe you are right, maybe it didn't install right and I should use unetbootin and install OS on Linux desk op instead. But then maybe Tha won't help anything. It's not guaranteed that it's not a mobo bios doesn't like booting o USB issue.

Also, OP didn't specify how he installed OS, could be he used unetbootin. Also burn to flash drive lmfao WHUT, flash drive = flash memory, no read and write laser. You could say install OS to flash drive, don't think the term "burn" woks. :confused:

---

### Post by Gremlinzzz on 2012-02-29
> **imachavel said:**
> :popcorn: you seem to have xperience.

But it's as though you didn't read the thread. We both have working flash drives, in fact I can put files on mine(which is strange because the drive is partitioned, flash memory partition wonder how the contiguous area works) and OS boot sector and grub are there. Maybe you are right, maybe it didn't install right and I should use unetbootin and install OS on Linux desk op instead. But then maybe Tha won't help anything. It's not guaranteed that it's not a mobo bios doesn't like booting o USB issue.

Also, OP didn't specify how he installed OS, could be he used unetbootin. Also burn to flash drive lmfao WHUT, flash drive = flash memory, no read and write laser. You could say install OS to flash drive, don't think the term "burn" woks. :confused:

:popcorn: woks.LOL

---

### Post by coolman98 on 2012-02-29
try a different flash drive?

---

### Post by improvent363 on 2012-03-05
> **imachavel said:**
> Also, OP didn't specify how he installed OS, could be he used unetbootin. Also burn to flash drive lmfao WHUT, flash drive = flash memory, no read and write laser. You could say install OS to flash drive, don't think the term "burn" woks. :confused:

I tried both methods separately and both failed: pendrivelinux and unetbootin. I used a laptop to install both of them.

---

### Post by improvent363 on 2012-03-05
> **coolman98 said:**
> try a different flash drive?


don't have a extra flash drive currently. 

So is their any way to try using the "nomodeset" [cuz for me that works with my live ubuntu cd] on the flash drive, since the usual method doesn't work?

---

### Post by HiImTye on 2012-03-05
[this]("http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html") should work for you. follow the 'liveCD' section and replace 'press a key' with 'hold shift'

---

