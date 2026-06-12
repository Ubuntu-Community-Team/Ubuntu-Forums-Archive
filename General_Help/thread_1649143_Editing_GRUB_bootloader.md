---
title: "Editing GRUB bootloader?"
date: 2010-12-19
forum: General Help
---

### Post by matt-fender on 2010-12-19
Hi guys, i almost have my 10.04 set-up exactly how I want it, but one thing is bugging me like crazy.

when i first boot up, my GRUB menu highlights Ubuntu 2.6.32-26-generic first, which is brilliant. However i noticed i have another kenel option to boot from, I think it was the kernel before my current (2.6.32-26-generic). Also the time-out is 30 seconds.

Is there any way I can remove the old Kernel line? ( is this safe to do so )

Is there any way I can reduce the time-out to a lower time? 10 seconds would be perfect?

I had a quick browse on the web and found a few posts but every file I opened to edit grub was empty?

Thanks in advance!

---

### Post by PhantmKllr on 2010-12-19
"System -> Administration -> Computer Janitor" in the main menu. That should remove the old kernel. I don't know much about editing the GRUB boot menu though.

---

### Post by Shintek on 2010-12-19
gksudo gedit /boot/grub/grub.cfg

---

### Post by matt-fender on 2010-12-19
> **PhantmKllr said:**
> "System -> Administration -> Computer Janitor" in the main menu. That should remove the old kernel. I don't know much about editing the GRUB boot menu though.

Hi PhantmKllr,

I took a look in Computer Janitor and couldn't find anything regarding the old kernel :(

---

### Post by matt-fender on 2010-12-19
> **Shintek said:**
> gksudo gedit /boot/grub/menu.lst

Paste that in your terminal, it will ask for a password, type in and press Return/Enter
Note: you cannot see what you are typing.

Be carefull while editing it!


Hey Shintek thanks for posting..

Punched her into a terminal, displaying an empty menu.lst file?

---

### Post by PhantmKllr on 2010-12-19
> **matt-fender said:**
> Hi PhantmKllr,

I took a look in Computer Janitor and couldn't find anything regarding the old kernel :(
Then, it's already been un-installed. Now follow @Shintek's instructions to remove the grub boot option.

---

### Post by kgarbutt on 2010-12-19
Hey Matt,

Use Ubuntu-Tweak and it will clean the old kernels.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

You'll download a deb file just open it and install. It is the best way to get the most recent version.

It will install under Applications>System Tools

Once you have opened Ubuntu-Tweak go to 'Package Cleaner' and clean everything including the old kernels.

---

### Post by Shintek on 2010-12-19
> **matt-fender said:**
> Hey Shintek thanks for posting..

Punched her into a terminal, displaying an empty menu.lst file?
Hey Matt, I edited my solution, should work now

If it asks for a password just type in your ROOT password, but you cannot see what you are typing

Be carefull editing it!

---

### Post by x1a4 on 2010-12-19
Hi,

Use the package manager (Synaptic, apt-get or aptitude) to remove unwanted kernels, this will also remove them from your GRUB menu.  Once the kernels are removed, open the GRUB menu for editing (the way Shintek showed you) and look for a line saying **timeout** and change the value (in seconds) to the right of it.  It should be close to the top below **default** which in turn specifies which kernel should load by default.

---

### Post by matt-fender on 2010-12-19
Brilliant!!! I am a happy chappy! thanks everyone for the speedy replies and help!

---

### Post by Shintek on 2010-12-19
> **matt-fender said:**
> Brilliant!!! I am a happy chappy! thanks everyone for the speedy replies and help!
You're welcome (not as in taking all the credit lol)

Thats the Ubuntu/Linux community! :popcorn:

---

