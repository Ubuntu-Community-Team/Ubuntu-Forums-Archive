---
title: "When mounting with uuid, external drive shows up in nautilus even when not plugged in"
date: 2010-04-20
forum: General Help
---

### Post by pwn on 2010-04-20
I have two 1TB Seagate USB (sdc1 and sdd1) drives connected to an old PC without an X server running.

Since sdc1 and sdd1 change depending on the order in which they are plugged in, I decided to mount them using their UUID instead.

These are my fstab entries

UUID=d1b28578-451b-4f03-af28-2e8a6d5b7efb /media/Seagate ext3 defaults,rw,auto,users
UUID=36bf5df4-934e-42d4-9e25-16a13971509c /media/Projects ext3 defaults,rw,auto,users

They work fine, but when I unmount them and unplug the USB drives, they still show up in Nautilus (I'm running nautilus with X11 forwarding onto another Ubuntu machine, btw).

Now if I remove those entries from fstab, the drives disappear from Computer. If I add the entries back, they show up as an unmounted drive even when the drive is not plugged in. How do I do this so they don't show up when they're not plugged in?

---

### Post by Morbius1 on 2010-04-20
I'm fairly certain that you need to change "auto" to "noauto".

You don't want the external drive to "auto" mount when it's not there.

With the "noauto" option , it will only mount when inserted.

You might want to change the "users" option to "user" as well unless you have multiple "users" on your box.

---

### Post by Drenriza on 2010-04-20
you should use following options
 
```
defaults, noauto, rw,
```
 
for further info try look here
[http://ubuntuforums.org/showthread.php?t=1457151&page=2](http://ubuntuforums.org/showthread.php?t=1457151&page=2)
reply #15

---

### Post by pwn on 2010-04-20
I tried noauto and the behaviour is the same. The drive is still showing up in Computer when it's not plugged in.

---

### Post by Morbius1 on 2010-04-20
This may be another one of those embarrassingly frequent cases where I didn't read the original post carefully enough. 

>  ... drives connected to an old PC without an X server running.

... but when I unmount them and unplug the USB drives, they still show up in Nautilus (I'm running nautilus with X11 forwarding onto another Ubuntu machine, btw).It should be gone under "Places" but of course the mount point ( /media/Seagate) will never go away because it's not being created "on-the-fly" - you created them yourself. If you want it to go away then return Ubuntu to it's original state and don't have any entry in fstab for those external hard drives.

---

### Post by pwn on 2010-04-20
I'm not talking about the mount point. I'm talking about "Computer" (Places > Computer). The unplugged drive shows up there. If I don't use the UUID for mounting then the drives don't show up. If I use the UUID, the drive is shown there.

---

### Post by Morbius1 on 2010-04-20
Hmm.. I wonder if it's this bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

The work around there ( aside from using /dev/sdxy ) was to change the fstab line this way:

[COLOR=Blue]/dev/disk/by-uuid/[/COLOR]d1b28578-451b-4f03-af28-2e8a6d5b7efb /media/Seagate ext3 defaults,rw,noauto,users

---

### Post by pwn on 2010-04-20
Tried it. Still the same problem.

---

### Post by egalvan on 2010-04-20
> **pwn said:**
> 
Now if I remove those entries from fstab, the drives disappear from Computer. 

USB drives should auto mount on being plugged in and detected.
They should show up with the device name.

Are you saying your USB drives do not automount if the entries are not in fstab?


> If I add the entries back, they **show up as an unmounted drive** even **when the drive is not plugged **in.

Isn't this the correct/expected behavior?

---

### Post by pwn on 2010-04-20
> **egalvan said:**
> 
Are you saying your USB drives do not automount if the entries are not in fstab?


Yes, which is probably because I'm running Nautilus over a remote session.



> **egalvan said:**
> 

Quote:
If I add the entries back, they show up as an unmounted drive even when the drive is not plugged in.

Isn't this the correct/expected behavior?

No, the drives should not show up if they aren't plugged in. 

If I mount them from fstab using the device name (/dev/sdc1, /dev/sdd1) they don't show up when the drives aren't plugged in. They get mounted when I plug the drives in. (This is the intended behaviour)

If I mount them from fstab using the UUID, they show up even when the drive isn't plugged in, and when I plug the drives, each drive is shown twice (one mounted, one unmounted). (Not the intended behaviour)

It does indeed look like the bug mentioned in [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130) and the workaround didn't work for me.

---

### Post by egalvan on 2010-04-20
> **pwn said:**
> Yes, which is probably because I'm running Nautilus over a remote session./quote]

Not running remote, so no experience there. Sorry.


No, the drives should not show up if they aren't plugged in. 

**If I mount them from fstab using the device name (/dev/sdc1, /dev/sdd1)** they don't show up when the drives aren't plugged in.
They get mounted when I plug the drives in. (**This is the intended behaviour)**

**If I mount them from fstab using the UUID**, they show up even when the drive isn't plugged in,
 and when I plug the drives, each drive is shown twice (one mounted, one unmounted). (**Not the intended behaviour)**


An idea...
Try mounting from fstab using** LABEL**
instead of using device name or UUID.


It's how I manage all my devices on my machines...
easier to use/remember/recognize than UUID, although I have to manage the "unique" aspect.

---

### Post by pwn on 2010-04-20
Tried. Still the same problem.

---

### Post by pwn on 2010-04-20
I got automount to work for remote users by editing /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

```
  <action id="org.freedesktop.devicekit.disks.filesystem-mount">
    <description>Mount a device</description>
    <description xml:lang="da">Montér en enhed</description>
    <description xml:lang="de">Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>[COLOR="Red"]**yes**[/COLOR]</allow_any>
      <allow_inactive>[COLOR="Red"]**yes**[/COLOR]</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>
```

---

