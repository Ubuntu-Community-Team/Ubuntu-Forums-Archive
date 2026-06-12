---
title: "Installing NVIDIA Without Jockey, NOT OFFICIAL DRIVERS."
date: 2010-10-31
forum: General Help
---

### Post by Lucradia on 2010-10-31
I want the drivers that are downloaded with jockey, but without having to use jockey-gtk (as it requires GNOME, and not just GTK.)

How do I go about downloading/installing said drivers for a restricted NVIDIA (GTX 470) video card for 3D Composition? (I noticed there's a package called jockey-common, but so far, all I've hit on google are bug reports related to jockey-gtk, and nothing on how to use the jockey-backend, alone.)

I can't start installing my openbox only (no-DE) install of ubuntu mini.iso without knowing how. The official drivers usually cause the entire system to start lagging for some reason on any brand of video card, ATI, NVIDIA and even Intel if I use the official BINs for each.

---

### Post by Lucradia on 2010-10-31
bump

---

### Post by P4man on 2010-10-31
have you tried

```
sudo jockey-text -c
```

(use -h for options)

---

### Post by Lucradia on 2010-10-31
Do I just need jockey-common to use jockey-text, or do I need one of the front-ends? Also, found some other useful whatnot:

List Drivers:
```
sudo jockey-text -l
```

Enable Current NVIDIA:
```
sudo jockey-text -e xorg:nvidia-current
```

---

### Post by P4man on 2010-10-31
I have no idea. I just typed in jockey and hit TAB key :).
I imagine jockey-common is all you need, but why dont you try?

---

### Post by Lucradia on 2010-10-31
> **P4man said:**
> I imagine jockey-common is all you need, but why dont you try?

Ok, thanks. I'll check it out shortly.

---

### Post by Lucradia on 2010-10-31
Looks like grub failed to install using the mini.iso. My CLI ubuntu is sitting there, unable to be booted into, as the GRUB bootloader screen won't appear at all (not even a split-second flash.)

---

### Post by Lucradia on 2010-10-31
grub-pc was still installed. I did
```
sudo apt-get install grub
```

using Super GRUB 2, rebooted, and windows still boots rather than showing the GRUB menu. Guess I'll try rescatux.

---

### Post by Lucradia on 2010-10-31
seems I needed to install grub2, not grub. You'd think that grub would be renamed grub-legacy and grub2 renamed to grub. Whatever.

it seems that when I update using jockey-text, it doesn't show any drivers that my GTX 470 can use. Is there some package I forgot to download?

Well, regardless, I'll just install nvidia-current, as it seems to be what I need.

---

### Post by Lucradia on 2010-10-31
After installing nvidia current, jockey says it's there, but can't enable:

```
user@24-241-225-222:~$ sudo jockey-text --list
[sudo] password for user: 
kmod:nvidia_current - nvidia_current (Proprietary, Enabled, Not in use)
user@24-241-225-222:~$ sudo jockey-text -e nvidia
Unknown driver: nvidia
Use --list to see available drivers
user@24-241-225-222:~$ sudo jockey-text -e nvidia_current
Unknown driver: nvidia_current
Use --list to see available drivers
user@24-241-225-222:~$ sudo jockey-text -e nvidia-current
Unknown driver: nvidia-current
Use --list to see available drivers
user@24-241-225-222:~$ sudo jockey-text -e xorg:nvidia-current
Unknown driver: xorg:nvidia-current
Use --list to see available drivers
user@24-241-225-222:~$ sudo jockey-text -e xorg:nvidia_current
Unknown driver: xorg:nvidia_current
Use --list to see available drivers
user@24-241-225-222:~$
```

Edit: People really need to write guides for these... I needed to install these as well,
```
sudo apt-get install nvidia-common nvidia-current-modaliases
```

Now jockey-text says:
```
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Enabled, In use)
```

Now, it's time to rock-and-roll.

---

