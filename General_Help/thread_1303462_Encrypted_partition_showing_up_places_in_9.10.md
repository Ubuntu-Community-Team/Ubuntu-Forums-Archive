---
title: "Encrypted partition showing up places in 9.10"
date: 2009-10-28
forum: General Help
---

### Post by mahousaru on 2009-10-28
I've just started testing 9.10.  My normal build has a fully encrypted partition using luks dmcrypt.

I partition my device as follows:

sda1 - /boot
sda2 - luks - lvm - (swap and /)

This still words fine, but now the encrypted volume gets displayed in Nautilus and in Places... 

[IMG]http://img443.imageshack.us/img443/7647/places.png[/IMG]

Trying to mount the device shows:

[IMG]http://img692.imageshack.us/img692/5610/placesauthenticate.png[/IMG]

As you can see it is shows the device it is trying to mount which is:

/dev/mapper/sda2_crypt

Any idea of how I can hide this please?

---

### Post by Giblet5 on 2009-10-28
That seems to be the correct behavior (to me anyway).

Places shows the available volumes.

That volume is available.

An encrypted filesystem is easily detected by anyone that really wants access, so hiding it where the drag-n-drool crowd won't spot it is pointless since they can't do anything with it anyway...except get it drooly.

If you're that paranoid, take a look at TrueCrypt's invisible shadow filesystem methodology.

---

### Post by mahousaru on 2009-10-28
It is not about paranoia, but about having a clean interface.  

I've used the same methodology of FDE since 7.04 and this is the first time that one of the devices in the encryption chain appears in Places.  

The volume is very much **not available**, coz it is mounted by LVM and writing to it will foobar my lvm group containing my root and swap partitions.

Truecypt has a FDE for Windows, but I want to use Ubuntu ;)

---

### Post by Giblet5 on 2009-10-28
> **mahousaru said:**
> It is not about paranoia, but about having a clean interface.  

I've used the same methodology of FDE since 7.04 and this is the first time that one of the devices in the encryption chain appears in Places.  

The volume is very much **not available**, coz it is mounted by LVM and writing to it will foobar my lvm group containing my root and swap partitions.

Truecypt has a FDE for Windows, but I want to use Ubuntu ;)


But it shows up because the logical volume exists.

Places shows existing logical volumes. So do all of the file browsers I know of.

A clean interface is one that elegantly presents the full truth. You'll probably have to tweak your udev configuration to get the FoxNews/MSNBC version of Ubuntu. :rolleyes:

Udev is out of my skillset so far, but now I'm curious...

---

### Post by mahousaru on 2009-10-28
> **Giblet5 said:**
> But it shows up because the logical volume exists.

Places shows existing logical volumes. So do all of the file browsers I know of.

A clean interface is one that elegantly presents the full truth. You'll probably have to tweak your udev configuration to get the FoxNews/MSNBC version of Ubuntu. :rolleyes:

Udev is out of my skillset so far, but now I'm curious...

Hmmm this is not the behaviour on my 9.04 box.  If I ls /dev/mapper I get the following:

control
lvm-root
lvm-swap
sda2_crypt

None of these devices are displayed in Places (or Nautilus).

On my 9.10 box the same devices exist but for some reason sda2_crypt is shown in Places and Nautilus.

Now if this was the case from previous versions then I would be fine with it, but it is not.  This has just appeared in 9.10!

The org I work for deals with a lot of sensitive data, hence the use of FDE and pushing out an unclean interface is not a good thing.

---

### Post by Giblet5 on 2009-10-28
> **mahousaru said:**
> Hmmm this is not the behaviour on my 9.04 box.  If I ls /dev/mapper I get the following:

control
lvm-root
lvm-swap
sda2_crypt

None of these devices are displayed in Places (or Nautilus).

On my 9.10 box the same devices exist but for some reason sda2_crypt is shown in Places and Nautilus.

Now if this was the case from previous versions then I would be fine with it, but it is not.  This has just appeared in 9.10!

The org I work for deals with a lot of sensitive data, hence the use of FDE and pushing out an unclean interface is not a good thing.


I agree that it is odd. I also argue that the 9.10 way is the correct way, even if it is inconvenient.

Karmic does lots of things differently from 9.04.

Try this: Wait until Karmic is released and not just RC, then if the behavior is the same as now, file a bug report on launchpad and see what the team says about it. I suspect they'll say what I did, but maybe not.

As a final resort, 9.04 will be oficially supported for a loooong time.

---

### Post by mahousaru on 2009-10-28
> **Giblet5 said:**
> I agree that it is odd. I also argue that the 9.10 way is the correct way, even if it is inconvenient.

Karmic does lots of things differently from 9.04.

Try this: Wait until Karmic is released and not just RC, then if the behavior is the same as now, file a bug report on launchpad and see what the team says about it. I suspect they'll say what I did, but maybe not.

As a final resort, 9.04 will be oficially supported for a loooong time.

I'll have to hold my horses a few more days before I can continue with my plan to overthrow SLED as the official supported nix where I work :)

---

