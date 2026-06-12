---
title: "indestructible config file?"
date: 2009-12-30
forum: General Help
---

### Post by danastasio on 2009-12-30
Hello all!

My problem seems to be unique. A while ago (Hardy)  I config'd grub to wait 2 seconds in a hidden menu then boot into Hardy w/o question. This was great for me. I then tried multiple distros and stayed with Arch for a while. I formatted the ENTIRE disk MANY times with this (its not easy to configure) and when i came back to Ubuntu as my only distro, even after I COMPLETLEY FORMATTED THE ENTIRE DISK, It still gave me that same config file. Unless the standard was changed so that a two second wait in a hidden menu became standard, i think something is going screwy. I upgraded to Karmic recently and have noticed that the old config file somehow messed with the current one. At boot I get a single line that says "GRUB loading..." and then Ubuntu starts to boot. This is fine because I dont have another OS. But I cannot access previous kernels or the "OH CRAP" session. 

Can anyone help me kill this immortal config file and return GRUB to normal for me?

---

### Post by phillw on 2009-12-30
Hi,

When you say 'upgraded to 9.10" - did you upgrade (in which case you're on grub legacy) or do  a fresh installation of 9.10 (in which case you're on Grub2) ?

```

grub-install -v
```0.9x = Grub Legacy
1.9x = Grub 2

Regardless of which you're on - you should go to Grub2. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Has a good section on it - along with links in drs305's Sig for all sorts of tweaks etc you can do with Grub2.

Regards,

Phill.

---

### Post by danastasio on 2009-12-30
Both actually, though with this iteration of the problem, it is a clean install.

```
dave@dave-laptop:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

```

And I didn't touch the grub.cfg file.

I'll check that link, thanks!

---

### Post by danastasio on 2009-12-30
wow... that answered my question in less than a minuet... wish i had thought of that on my own xD

That doesn't explain how the legacy settings are always prevalent though.

---

### Post by dcstar on 2009-12-31
> **danastasio said:**
> wow... that answered my question in less than a minuet... wish i had thought of that on my own xD

That doesn't explain how the legacy settings are always prevalent though.

Who said they are, that is normal Grub2 behaviour.

Hold down Shift if you want a menu.

---

