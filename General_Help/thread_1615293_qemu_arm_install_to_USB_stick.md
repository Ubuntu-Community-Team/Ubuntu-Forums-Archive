---
title: "qemu arm install to USB stick?"
date: 2010-11-06
forum: General Help
---

### Post by MrUmunhum on 2010-11-06
Hi group,
I would like to run Ubuntu for an ARM processor under Qemu under Fedora 13. I have followed the instruction on: [http://https://wiki.ubuntu.com/ARM/OMAPMaverickInstall]("http://https://wiki.ubuntu.com/ARM/OMAPMaverickInstall") but when I try to boot, I get a message that says "Kernel image must be specified". I am using virt-manager to build the VM.
This is the log entry:[INDENT]
LC_ALL=C PATH=/sbin:/usr/sbin:/bin:/usr/bin QEMU_AUDIO_DRV=none /usr/bin/qemu-system-arm -S -M integratorcp -no-kvm -m 512 -smp 1,sockets=1,cores=1,threads=1 -name sdb -uuid 205ac400-e8f4-af87-9f22-9a2c78a4e3ea -nodefaults -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/sdb.monitor,server,nowait -mon chardev=monitor,mode=readline -rtc base=utc -boot c -drive file=/dev/sdb,if=none,id=drive-ide0-0-0,boot=on,format=raw -device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -device rtl8139,vlan=0,id=net0,mac=52:54:00:f0:b2:8b,bus=pci.0,addr=0x4 -net tap,fd=40,vlan=0,name=hostnet0 -chardev pty,id=serial0 -device isa-serial,chardev=serial0 -usb -vnc 127.0.0.1:0 -vga cirrus -device AC97,id=sound0,bus=pci.0,addr=0x5 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x3 
char device redirected to /dev/pts/2
Kernel image must be specified[/INDENT]

Does this mean there is no MBR??

---

