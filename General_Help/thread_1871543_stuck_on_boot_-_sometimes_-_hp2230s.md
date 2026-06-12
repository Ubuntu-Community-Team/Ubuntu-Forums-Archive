---
title: "stuck on boot - sometimes - hp2230s"
date: 2011-10-29
forum: General Help
---

### Post by daniel227 on 2011-10-29
hello,

my girlfriend uses ubuntu 10.04 (with updates, no upgrades).

sometimes the boot process gets stuck with a blank screen, sometimes after login.
rebooting usually helps, but sometimes it takes a few tries.
it's rather random but she says the problem always occurs when she presses the mute/unmute button during startup.

any help?

thx-

daniel

the hardware is an hp 2230s small laptop with a 12" screen. it originally had windows vista and she installed ubuntu from a cd from a downloaded .iso

---

### Post by WasMeHere on 2011-10-29
Hello daniel227,

Why is she pressing the mute/unmute button during startup?

Have fun finding out about Ubuntu :-)
Olle

---

### Post by daniel227 on 2011-10-30
thanks olle.

what i meant is: it happens randomly (without doing anything to make it happen), but it happens most definitely when pressing mute/unmute during startup.

however, the latter doesn't apply anymore because i changed the setup to automatic login and disabled the login sound.

for the first part, we have to see how things develop now.

---

### Post by WasMeHere on 2011-10-30
Hello again,

Keep in touch if the problem occurs again.

Maybe you can do the following checks.

Run from a live disk (for example the install CD). Do *not* mount any partition of the hard drive. Use *fdisk* to find out which is your Ubuntu partition. ```
sudo fdisk -lu
``` Then use *e2fsck* to check that your partition is clean ```
sudo e2fsck /dev/sda[COLOR="Red"]x[/COLOR]
``` where [COLOR="Red"]x[/COLOR] should be substituted with the number found by *fdisk*.

And then update (within 10.04 LTS)
```
sudo apt-get update
sudo apt-get upgrade
```

Good luck
Olle

---

### Post by daniel227 on 2011-11-01
thx, it's been fine now for a while, knock on wood!

---

