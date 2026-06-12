---
title: "Grub problems Help!!"
date: 2011-04-06
forum: General Help
---

### Post by djRif on 2011-04-06
Hi Guys

I hope some Ubuntu/Linux kind genius can help me!
I have an Alienware M11x r2 laptop running Windows 7-63 and Ubuntu 10.10 Unity installed

It was all fine and dandy until I changed my grub timeout to 1 sec (or perhaps 0, its been so long i can't remember!) to reduce the waiting time until an OS boots...
My grub was set to boot to Windows 7 as default...

Now when I boot up I cannot halt the boot process not matter what key I press (e.g SHIFT)... I am doomed to forever boot into Windows. Its been months and I had written off my Ubuntu OS but I am tempted to try and fix this one more time...

Since I cannot access the Ubuntu installation AT ALL I cant use the usual ways to increase the timeout on the grub menu (yes I have searched the forums far and wide)...

Is there ANY way of changing the grub menu parameters without actually booting into Ubuntu Unity? Can I modify the timeout settings using a live cd or usb boot?

Sorry for my noob comments. Any help will be appreciated.

Many thanks!!

Rif

---

### Post by Dutch70 on 2011-04-06
lol, the things we do with our Ubuntu. :)

Have you tried reinstalling Grub2 from the live cd/usb? I'm not sure if it would solve your problem or not, but it's easy enough to try.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Also, have you tried hitting the "escape" key while booting?

---

### Post by Hedgehog1 on 2011-04-07
If the re-install of grub does not reset the timer to 10 seconds, you can alter the setting yourself.

Please boot off the LiveCD/Live USB, select 'TRY', and then:

**NOTE-These command assume your Ubuntu '/' root partition is sda5, if yours is other please use that instead.**

```
sudo mount /dev/sda5 /mnt
```

```
gksudo gedit /mnt/etc/default/grub
```

[COLOR="Red"]*and change:*[/COLOR]

GRUB_TIMEOUT=0

[COLOR="red"]*to:*[/COLOR]

GRUB_TIMEOUT=10

```
sudo grub-install --root-directory=/mnt /dev/sda
```

***The Hedge***

:KS

---

