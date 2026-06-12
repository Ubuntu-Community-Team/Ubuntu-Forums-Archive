---
title: "Cannot run the rootfs in UML successfully"
date: 2011-11-23
forum: General Help
---

### Post by ningji on 2011-11-23
i basically followed this
[https://help.ubuntu.com/community/UserModeLinux](https://help.ubuntu.com/community/UserModeLinux)
and made changes accordingly.

1. i can load a fedora rootfs in uml for i386
2. in ubuntu desktop (lucid)
sudo apt-get install user-mode-linux uml-utilities bridge-utils 
debootstrap

dd if=/dev/zero of=uml-root-hardy bs=4096 seek=100 count=1
mkfs -t ext3 rfs
sudo mount -o loop rfs /mnt
sudo -i
debootstrap --arch i386 lucid /mnt [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)
echo "/dev/ubd0  /       xfs     defaults     0 1" > /mnt/etc/fstab
echo "proc       /proc   proc    defaults     0 0" >> /mnt/etc/fstab
mknod --mode=660 /mnt/dev/ubd0 b 98 0
chown root:disk /mnt/dev/ubd0
echo "127.0.0.1 localhost" > /mnt/etc/hosts
echo "auto lo" > /mnt/etc/network/interfaces
echo "iface lo inet loopback" >> /mnt/etc/network/interfaces
echo "auto eth0" >> /mnt/etc/network/interfaces
echo "iface eth0 inet dhcp" >> /mnt/etc/network/interfaces 

echo "tty0" >> /mnt/etc/securetty
echo "ttys/0" >> /mnt/etc/securetty

# Remove the other terminal events
# forgot the details, but get rid of tty2 ~ tty6

exit 

3. run it
TUN/TAP backend - IP = 10.50.181.254
registered taskstats version 1
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with writeback data mode.
VFS: Mounted root (ext3 filesystem) readonly on device 98:0.
Warning: unable to open an initial console.
Kernel panic - not syncing: No init found.  Try passing init= option to kernel.
1146ff78:  [<083cca49>] panic+0x4d/0xfc
1146ff94:  [<0805e24e>] init_post+0xae/0x100
1146ffa8:  [<080491b5>] kernel_init+0xee/0xf5
1146ffbc:  [<0808c2b0>] run_kernel_thread+0x30/0x50
1146ffd8:  [<0808c29f>] run_kernel_thread+0x1f/0x50
1146ffe4:  [<0805fd2f>] new_thread_handler+0x6f/0xa0
1146ffe8:  [<080490c7>] kernel_init+0x0/0xf5


EIP: 0073:[<b76fc430>] CPU: 0 Not tainted ESP: 007b:bfb39f44 EFLAGS: 00000246
    Not tainted
EAX: 00000000 EBX: 000039d8 ECX: 00000013 EDX: 000039d8
ESI: 000039d4 EDI: bfb39fd0 EBP: 0000003b DS: 007b ES: 007b
1146ff54:  [<080b6fd1>] notifier_call_chain+0x41/0x60
1146ff78:  [<083cca65>] panic+0x69/0xfc
1146ff94:  [<0805e24e>] init_post+0xae/0x100
1146ffa8:  [<080491b5>] kernel_init+0xee/0xf5
1146ffbc:  [<0808c2b0>] run_kernel_thread+0x30/0x50
1146ffd8:  [<0808c29f>] run_kernel_thread+0x1f/0x50
1146ffe4:  [<0805fd2f>] new_thread_handler+0x6f/0xa0
1146ffe8:  [<080490c7>] kernel_init+0x0/0xf5

Terminated

---

