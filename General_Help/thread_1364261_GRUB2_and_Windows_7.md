---
title: "GRUB2 and Windows 7"
date: 2009-12-25
forum: General Help
---

### Post by Hwæt on 2009-12-25
Hi everyone, I recently installed Windows 7 to my second hdd while my first one with Linux on it was unplugged so that I wouldn't mess up the GRUB install. How can I get Windows 7 listed in the GRUB menu?

By the way, after I installed Windows 7 I noticed this in my file browser. What is it?

OS: Ubuntu 9.10

---

### Post by ranch hand on 2009-12-25
Are you using grub- legacy or grub2?  If you are not sure run:
```

grub-install -v

```
and post result here.

---

### Post by Hwæt on 2009-12-25
It's GRUB2, just like it says in the title.

---

### Post by Hwæt on 2009-12-25
I just tried:

```

update-grub2

```

but it wouldn't finish because I think that Windows 7 Ultimate's System Reserved partition is throwing it off.

Any workarounds?

---

### Post by hal8000 on 2009-12-25
You need to make a manul entry in grub.cnf for windows 7.

Start by typing

sudo fdisk -l

to list the partition where windows 7 is located.

Heres a guide that may help:

[https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg)

---

### Post by Hwæt on 2009-12-25
> **hal8000 said:**
> You need to make a manul entry in grub.cnf for windows 7.

Start by typing

sudo fdisk -l

to list the partition where windows 7 is located.

Heres a guide that may help:

[https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg)

I don't see anything about Windows 7 there.

Do I just take:

```

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
        set root=(hd0,1)
        chainloader +1
}

```

edit my details into it, and then stick it into 40_custom, since it says not to edit grub.cfg?

---

### Post by ranch hand on 2009-12-25
Is the drive with your MS install on it in your /boot/grub/device.map?

---

### Post by Hwæt on 2009-12-25
> **ranch hand said:**
> Is the drive with your MS install on it in your /boot/grub/device.map?

Well, this HDD wasn't plugged into my computer until recently. It wasn't even there when I originally installed karmic. Would this cause it not to show up there?

How do I edit it?

---

### Post by ranch hand on 2009-12-25
```

gksudo gedit /boot/grub/device.map

```
Would be the way to do that.

After you do that re-run;
```

sudo update-grub

```

---

### Post by Hwæt on 2009-12-26
> **ranch hand said:**
> ```

gksudo gedit /boot/grub/device.map

```
Would be the way to do that.

After you do that re-run;
```

sudo update-grub

```

That worked perfectly! Thank you very much!

---

### Post by ranch hand on 2009-12-26
Great.  I like the easy ones.

You might be interested in the link in my sig.  It is meant to be a simple overview.  There are a lot of links, all good information, the first 2 are the best in depth sources for grub2.  A good bit of the wiki info comes from those as a base and drs305 has his synced (I believe) with the wiki (hisis the 2nd link - great stuff).

A bunch of us are from Karmic-testing.  Grub2 was introduced in Alpha2.  It was a rough ride for a while and we all fought with it (no documentation).  We all, for about 2 weeks, edited the grub.cfg file as none of the entries worked.  Lots of kernel updates "encouraged" us to find a better way.  Herman (1st link) was a huge help as he had been fooling with grub2 for about a year.

Grub-legacy is great.  I love it.  It is not supported by anyone any more.  Grub2 is even better but you do have to learn a totally new way to deal with it.

With the right custom menu entries you can disable  every thing above 10_linux and have a very brief, clean, labeled menu that never needs to be updated unless you add an OS.

I am on my 10.04-testing platform and I have several OS' on it.  This is how it can look;
[quote]
#!/bin/sh
# This file is an example on how to add custom entries

echo "Adding Daily on sda13" >&2 
cat << EOF
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Lounge on sda7 Recovery" >&2 
cat << EOF
menuentry "Lounge on sda7 Recovery" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux    /boot/vmlinuz-2.6.32-7-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single 
    initrd    /boot/initrd.img-2.6.32-7-generic
}
EOF

echo "Adding Lxde on sda8" >&2 
cat << EOF
menuentry "Lxde on sda8" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding ISO on sda14" >&2 
cat << EOF
menuentry "ISO on sda14" {
    set root=(hd0,14)
        linux /vmlinuz root=/dev/sda14 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Mini on sda15" >&2 
cat << EOF
menuentry "Mini on sda15" {
    set root=(hd0,15)
        linux /vmlinuz root=/dev/sda15 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Throw on sda16" >&2 
cat << EOF
menuentry "Throw on sda16" {
    set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Krap on sda17" >&2 
cat << EOF
menuentry "Krap on sda17" {
    set root=(hd0,17)
        linux /vmlinuz root=/dev/sda17 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Zenix on sda11" >&2 
cat << EOF
menuentry "Zenix on sda11" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Stoner1.2 on sda12" >&2 
cat << EOF
menuentry "Stoner1.2 on sda12" {
    set root=(hd0,12)
        linux /vmlinuz root=/dev/sda12 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Main on sda6" >&2 
cat << EOF
menuentry "Main on sda6" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Main on sda6 (2.6.24-24-generic)" >&2 
cat << EOF
menuentry "Main, kernel 2.6.24-24-generic (sda6)" {
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-24-generic
}
EOF

echo "Adding Mandriva on sda10" >&2 
cat << EOF
menuentry "Mandriva on sda10" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Man-Both on sda10" >&2 
cat << EOF
menuentry "Man-Both on sda10" {
        linux (hd0,10)/boot/vmlinuz
        initrd (hd0,10)/boot/initrd.img
}
EOF
[quote]
The Mandriva entry is an experiment that doesn't work.  The Man-both entry does work for that installation.  It is Mandriva 2009-1 and comes as a LiveDVD with Gnome, Lxde and KDE on it.  You can install one or all of them.  I did them all.  I call it both because I rarely use KDE.

MAIN is Hardy that I started with.

---

