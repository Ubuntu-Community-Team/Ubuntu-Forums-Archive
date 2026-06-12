---
title: "Where is the latest kernel?"
date: 2006-04-21
forum: General Help
---

### Post by Hoffmann on 2006-04-21
Hi:

By the way, is the latest stable (686) kernel going to be release for updating on the Ubuntu Breeze 5.10?

My kernel is: 2.6.12-10-686-smp

Hoffmann

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=Hoffmann]Hi:

By the way, is the latest stable (686) kernel going to be release for updating on the Ubuntu Breeze 5.10?

My kernel is: 2.6.12-10-686-smp

Hoffmann[/QUOTE]
No, the kernel in the repositories is the kernel that Breezy was designed with and it stays with that kernel. You can follow the tutorial I wrote (link is in my signature) and compile the latest kernel from kernel.org 2.6.16.9 (Stable). You can even import your old kernel configuration. New kernels offer enhanced performance and better support for hardware.

---

### Post by Hoffmann on 2006-04-21
[QUOTE=MasterChief1234]No, the kernel in the repositories is the kernel that Breezy was designed with and it stays with that kernel. You can follow the tutorial I wrote (link is in my signature) and compile the latest kernel from kernel.org 2.6.16.9 (Stable). You can even import your old kernel configuration. New kernels offer enhanced performance and better support for hardware.[/QUOTE]


Does your approach work for the 686-smp kernel too? If affirmative, what is the trick?

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=Hoffmann]Does your approach work for the 686-smp kernel too? If affirmative, what is the trick?[/QUOTE]
You would basically take the kernel source and set it up as your new kernel. You can configure it for speed. You can select multicore/symetric processing for processors that support it.

---

### Post by Hoffmann on 2006-04-21
[QUOTE=MasterChief1234]You would basically take the kernel source and set it up as your new kernel. You can configure it for speed. You can select multicore/symetric processing for processors that support it.[/QUOTE]


When I type:

sudo make xconfig

I get:
make: *** No rule to make target `xconfig'.  Stop.

So, how coud I configure the kernel?

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=Hoffmann]When I type:

sudo make xconfig

I get:
make: *** No rule to make target `xconfig'.  Stop.

So, how coud I configure the kernel?[/QUOTE]
Did you follow all the steps ? And are you in usr/src/linux with fill root acess ?

---

### Post by adamkane on 2006-04-21
Note:
Only upgrade if you prefer speed over functionality. You probably already have the latest functional kernel already.

Again you will lose functionality if you upgrade to the latest bleeding-edge kernel. Here is a way to upgrade to the latest functional kernel.

Check your kernel version:
```

uname -r

``` 
This should say:
2.6.12-10-686 or 2.6.12-10-k7

To get the latest functional kernel for your hardware:

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

``` 
AMD K Series (Duron, Athlon, Sempron):
 ```

 sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7
 
``` 
Older legacy PC (Intel Pentium Pro or 486):
 ```

 sudo apt-get install linux-386 linux-headers-386 linux-image-386 linux-restricted-modules-386
 
```

Reboot.

---

### Post by Hoffmann on 2006-04-21
[QUOTE=adamkane]Note:
Only upgrade if you prefer speed over functionality. You probably already have the latest functional kernel already.

Again you will lose functionality if you upgrade to the latest bleeding-edge kernel. Here is a way to upgrade to the latest functional kernel.

Check your kernel version:
```

uname -r

``` 
This should say:
2.6.12-10-686 or 2.6.12-10-k7

To get the latest functional kernel for your hardware:

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

``` 
AMD K Series (Duron, Athlon, Sempron):
 ```

 sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7
 
``` 
Older legacy PC (Intel Pentium Pro or 486):
 ```

 sudo apt-get install linux-386 linux-headers-386 linux-image-386 linux-restricted-modules-386
 
```

Reboot.[/QUOTE]

Thanks for the explanations.
Well, I wrote:

```

sudo apt-get install linux-686-smp

``` 
And I got:

Reading package lists... Done
Building dependency tree... Done
linux-686-smp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So, it seems like I am all right.

One question:

What about the upgrade from Breeze to Dapper? Is the current kernel going to work? Or  is Dapper going to 'install' another ('default') kernel?

Hoffmann

---

### Post by adamkane on 2006-04-21
Dapper seems to do a decent job installing the correct kernel for your hardware. As always, check with uname -r.

---

