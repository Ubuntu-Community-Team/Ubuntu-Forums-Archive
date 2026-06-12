---
title: "PXEboot Fedora from Ubuntu"
date: 2011-10-02
forum: General Help
---

### Post by ptmuldoon on 2011-10-02
I'm learning more and more about PXE booting, and my Ubuntu server is now capable of installing both Ubuntu and Windows7 to a spare laptop.

Now, I'm looking to learn and add some additional OS's to it.  Thus, I'm looking to add Fedora to the list, and than eventually some others.

But I'm unsure what I need add regarding the kernel and append to the my pxelinux.cfg/default file.  I've started with this, but pretty sure its not correct

```

LABEL Fedora15
        kernal Fedora/15/i686/vmlinuz
        APPEND method=nfs:path_to_Fedora/15/i386/ lang=us keymap=us ip=dhcp ksdevice=eth0 noipv6 initrd=Fedora/15/i686/initrd.img ramdisk_size=10000

```

Has anyone added Fedora to a PXEBoot setup?

---

