---
title: "Can't boot after BURG installation failed. PANIC"
date: 2010-11-01
forum: General Help
---

### Post by jvacek996 on 2010-11-01
Alright, here is the deal.

I just recently stumbled upon a post on OMG Ubuntu about installing Burg ([http://212.67.217.103/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/#comment-92661627](http://212.67.217.103/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/#comment-92661627)), so i went and tried it.

all of the steps went alright, until i typed in ```
sudo burg-install “(hd0)”
```
where i replaced "(hd0)" with "/dev/sda1"

then it gaver me an error > /usr/sbin/burg-probe: error: cannot find a device for /boot/burg (is /dev mounted?)

after that my batter ran out, and i rebooted - one thing i shouldnt've had let happened.
so i rebooted, and even before the windows system thingy spawned, the grub told me that some disc with a horrible number couldnt be found, and gave me a grub rescue line.

Now i'm on my father's computer, downloaded the Maverick meerkat iso, and burnt it. i also downloaded and burnt supergrubdisc2, which i thought might maybe help.

So now i am in the Meerkat CD, trying to set things back.
I already truied to re-install burg, but it always told me that /dev migh not be mounted, and when i tried to install grub, it told me that /dev isnt mounted again.

I am really forked if I don't get this machine working in the next week or so, so i am trying any thing that might help.

So, if you have an anwser to any of the following, i will owe you one, a big one.

-- is there a way to mount dev (my normal internal hard disk) if i am runnig from a CD?
-- is there a way to succesfully install either BURG or GRUB while running ubuntu from a CD?
-- 

some things that might possibly give you some greater detail.

I have a HP Compaq 6730s, with Windows 7 installed and Ubuntu 10.10 upgraded from 10.04

My Ubuntu Installation is from a Wubi.

I am czech, so please understand that i am not a native english speaker and grammar is not perfect

---

### Post by timgood on 2010-11-01
[This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") may help - it has helped me in the past! 

Let me know if you get stuck - hope things turn out well...

---

### Post by jvacek996 on 2010-11-01
there is just one problem, my ubuntu was installed via wubi, so if i want to access the ubuntu files from the outside, i would have a "root.disk" and a "swap.disk". do you know any way to acess these inside a ubuntu live cd? ill check google as well

---

### Post by bcbc on 2010-11-01
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
(Ignore warnings relating to booting linux)

That will get windows booting (using lilo instead of the windows bootloader - wubi installs need the windows or equivalent bootloader in the MBR).

To view the root.disk from windows download ext2read and point it at the root.disk.

Although wubi should boot again provided the grub.cfg is still there. Once booted, reinstall grub-pc (remove burg) making sure you DON'T install grub to /dev/sda or any other device.

---

### Post by jvacek996 on 2010-11-02
OMG YOU HAVE NO IDEA HOW MUCH YOU HELPED ME!!!!!!
I BOOTED INTO WINDOWS _AND EVEN UBUNTU_ THE USUAL WAY!
I LOVE YOU, AND OWE YOU A BIG ONE!

I will just remove BURG via synaptic manager.

Once again, thank you soooo much!

**Hope this thread helps anyone else who tried to install burg with a wubi and it failed.**

---

### Post by dcstar on 2010-11-02
> **jvacek996 said:**
> Alright, here is the deal.

I just recently stumbled upon a post on OMG Ubuntu about installing Burg ([http://212.67.217.103/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/#comment-92661627](http://212.67.217.103/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/#comment-92661627)), so i went and tried it.

all of the steps went alright, until i typed in ```
sudo burg-install &#8220;(hd0)&#8221;
```
where i replaced "(hd0)" with "/dev/sda1"

then it gaver me an error 
.........
This will set up everything correctly:
```
sudo dpkg-reconfigure burg-pc
```
Do not just use what other people have put in blogs - that is for **their** particular hardware.

---

### Post by bcbc on 2010-11-02
> **dcstar said:**
> This will set up everything correctly:
```
sudo dpkg-reconfigure burg-pc
```
Do not just use what other people have put in blogs - that is for **their** particular hardware.

The point is that burg doesn't work with wubi.

---

### Post by bcbc on 2010-11-02
> **jvacek996 said:**
> OMG YOU HAVE NO IDEA HOW MUCH YOU HELPED ME!!!!!!
I BOOTED INTO WINDOWS _AND EVEN UBUNTU_ THE USUAL WAY!
I LOVE YOU, AND OWE YOU A BIG ONE!

I will just remove BURG via synaptic manager.

Once again, thank you soooo much!

**Hope this thread helps anyone else who tried to install burg with a wubi and it failed.**

Glad you got it sorted out :)

---

