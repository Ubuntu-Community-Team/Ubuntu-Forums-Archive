---
title: "Fix Boot File"
date: 2010-01-07
forum: General Help
---

### Post by rougy44 on 2010-01-07
Hi,

I recently repartitioned my disk and moved my swap file to the end.

I figured out how to get my swap file working again, but something in the boot process got messed up and I'd like to try to figure out what the error is.

From GRUB, it used to start up nice and pretty and clean and finally show the login menu.

But now it finds an error somewhere and starts rebooting from scratch in "verbose" mode I think it's called, where I can see all of the commands being executed.

Everything works fine once it boots up, but I'd really like to figure out how to make it work like it did before.

Thanks.

---

### Post by dcstar on 2010-01-07
> **rougy44 said:**
> Hi,

I recently repartitioned my disk and moved my swap file to the end.

I figured out how to get my swap file working again, but something in the boot process got messed up and I'd like to try to figure out what the error is.

From GRUB, it used to start up nice and pretty and clean and finally show the login menu.

But now it finds an error somewhere and starts rebooting from scratch in "verbose" mode I think it's called, where I can see all of the commands being executed.

Everything works fine once it boots up, but I'd really like to figure out how to make it work like it did before.

Thanks.

Try:
```
sudo update-grub
```

---

### Post by rougy44 on 2010-01-07
Thanks for the suggestion, but it didn't work.

I'm running Mint if that makes any difference.

Didn't think it would.

---

### Post by oldos2er on 2010-01-07
> **rougy44 said:**
> I recently repartitioned my disk and moved my swap file to the end.

The UUIDs probably changed. If you have a LiveCD, boot from it and run **sudo blkid** then edit your fstab inserting the correct UUID. You'll need to mount your root partition to do this, so commands would look something like

[B]sudo mkdir /media/mint
sudo mount /dev/sdXX /media/mint[/B] [where XX is the letter and number designation of your root partition. On my system it's sda5].
**sudo nano /media/mint/etc/fstab**

Once you've made the changes, hit Ctrl-X in nano, it will prompt you to save the file. Reboot, and hopefully everything should work.

---

### Post by rougy44 on 2010-01-07
Again, I appreciate the help very much. :)

I decided to strip out the UUIDs from the "fstab" file, and just use the SDA* data.  Didn't seem to hurt anything.

/dev/sda8 / ext3 relatime,errors=remount-ro  0  1

When I start ubuntu from grub I use "ro quiet splash"

Everything runs fine once it's up, but the quiet splash screen will not make it through to the end like it used to and I can't figure out where the hiccup is.

It used to be grub->splash screen->login.

Now it's grub->splash screen->verbose line-by-line->login.

It's a cosmetic annoyance, really, but I want to fix it.

---

### Post by oldfred on 2010-01-07
My entries were:

ro splash quiet

---

### Post by Leppie on 2010-01-07
i used to have "ro quiet splash" as well with the 2.6.31 kernels

---

### Post by rougy44 on 2010-01-07
Thanks oldFred and Leppie.

I tried both "ro quiet splash" and "ro splash quiet" and still the same thing.

Oh, well, guess this is a good excuse to upgrade.

---

