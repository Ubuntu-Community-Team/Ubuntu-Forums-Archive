---
title: "8gb Ipod Touch 1g not recognized on Lucid"
date: 2010-09-13
forum: General Help
---

### Post by |{urse on 2010-09-13
Okay so I was under the impression that lucid had plug and play out of the box support for iphone/itouch/ietc. So I formatted right over intrepid and did a clean install of 10.4. Well, long story short there's nothing in gui or mount stating that it had detected an ipod. I can rule out a failed usb port/cord/ipod as it is recognized by windows every time on the same laptop (acer aspire 5532). Ifuse and libimobiledevice are all installed as well as their depends. Any ideas?

---

### Post by Gunman1982 on 2010-09-13
Wich version of iOs are you running? Saw a thread here where somebody said that the new 4.1(?!) is not supported by libimobiledevices yet.

---

### Post by |{urse on 2010-09-13
Yeah, it's running 3.13 untethered jb with spirit

---

### Post by |{urse on 2010-09-13
I was just thinking.. If anyone knows of a good program for ubuntu that will create wifi hotspots ((easily) because I'm lazy) that would help also. All I really need to do with this ipod is get rw access to the filesystem via scp to bypass the need to have it physically mounted. So an ad-hoc connection would help too.

---

### Post by s.fox on 2010-09-13
> **Gunman1982 said:**
> Wich version of iOs are you running? Saw a thread here where somebody said that the new 4.1(?!) is not supported by libimobiledevices yet.

I have also seen nothing on the official [libmobiledevice]("http://www.libimobiledevice.org/") site about the latest iOS :( 

> Latest Release: 1.0.2
Tested with iPhone/iPod Touch 1G, 2G, 3G/3GS, iPhone 4 running up to firmware 4.0.2 and iPad running up to firmware 3.2.2

-Silver Fox

---

### Post by |{urse on 2010-09-13
Nope, it's firmware 3.13 so I shouldn't be having a problem with libimobiledevice. Surely theres got to be some other way here. And I'm not too keen installing windows and itunes in a vm just so I can edit files on an ipod, been there, done that.

---

### Post by Gunman1982 on 2010-09-13
Maybe check the following: plug in your ipod and execute the command 'dmesg | tail' in a console/terminal. Maybe gives you a hint what its doing or rather not doing.

---

### Post by |{urse on 2010-09-13
> [ 7630.228403] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb2/2-2/2-2:1.0/input/input12
[ 7630.228929] generic-usb 0003:046D:C03D.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-2/input0
[ 7631.860121] usb 1-1: new high speed USB device using ehci_hcd and address 8
[ 7631.999173] usb 1-1: configuration #1 chosen from 3 choices
[20127.143679] usb 1-1: USB disconnect, address 8
[20131.964088] usb 1-1: new high speed USB device using ehci_hcd and address 9
[20132.103114] usb 1-1: configuration #1 chosen from 3 choices
[20195.923649] usb 1-1: USB disconnect, address 9
[20199.628089] usb 1-1: new high speed USB device using ehci_hcd and address 10
[20199.767176] usb 1-1: configuration #1 chosen from 3 choices


Doesn't help much, but thats what dmesg says immediately after plugging it in.

> /dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


And I dont see any new filesystems after issuing the mount command.

> laptop:~/Downloads/libimobiledevice-1.0.1$ sudo lshw -businfo
[sudo] password for laptop: 
Bus info          Device      Class       Description
=====================================================
                              system      Aspire 5532
                              bus         Aspire 5532
                              memory      1MiB BIOS
cpu@0                         processor   AMD Athlon(tm) Processor TF-20
                              memory      128KiB L1 cache
                              memory      512KiB L1 cache
                              memory      3GiB System Memory
                              memory      2GiB DIMM DDR2 Synchronous 333 MHz (3.0 ns)
                              memory      1GiB DIMM DDR2 Synchronous 333 MHz (3.0 ns)
                              memory      DIMM DDR2 [empty]
                              memory      DIMM DDR2 [empty]
pci@0000:00:00.0              bridge      RS780 Host Bridge
pci@0000:00:01.0              bridge      RS780 PCI to PCI bridge (int gfx)
pci@0000:01:05.0              display     RS780M/RS780MN [Radeon HD 3200 Graphics]
pci@0000:00:04.0              bridge      RS780 PCI to PCI bridge (PCIE port 0)
pci@0000:02:00.0  wlan0       network     AR928X Wireless Network Adapter (PCI-Express)
pci@0000:00:05.0              bridge      RS780 PCI to PCI bridge (PCIE port 1)
pci@0000:08:00.0  eth0        network     Atheros AR8132 / L1c Gigabit Ethernet Adapter
pci@0000:00:11.0  scsi0       storage     SB700/SB800 SATA Controller [AHCI mode]
scsi@0:0.0.0      /dev/sda    disk        160GB Hitachi HTS54501
scsi@0:0.0.0,1    /dev/sda1   volume      12GiB Windows NTFS volume
scsi@0:0.0.0,2    /dev/sda2   volume      101MiB Windows NTFS volume
scsi@0:0.0.0,3    /dev/sda3   volume      98GiB Windows NTFS volume
scsi@0:0.0.0,4    /dev/sda4   volume      37GiB Extended partition
                  /dev/sda5   volume      36GiB Linux filesystem partition
                  /dev/sda6   volume      1639MiB Linux swap / Solaris partition
scsi@2:0.0.0      /dev/cdrom  disk        DVDRAM GT31N
pci@0000:00:12.0              bus         SB700/SB800 USB OHCI0 Controller
pci@0000:00:12.1              bus         SB700 USB OHCI1 Controller
pci@0000:00:12.2              bus         SB700/SB800 USB EHCI Controller
pci@0000:00:14.0              bus         SBx00 SMBus Controller
pci@0000:00:14.2              multimedia  SBx00 Azalia (Intel HDA)
pci@0000:00:14.3              bridge      SB700/SB800 LPC host controller
pci@0000:00:14.4              bridge      SBx00 PCI to PCI Bridge
pci@0000:00:18.0              bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration
pci@0000:00:18.1              bridge      K8 [Athlon64/Opteron] Address Map
pci@0000:00:18.2              bridge      K8 [Athlon64/Opteron] DRAM Controller
pci@0000:00:18.3              bridge      K8 [Athlon64/Opteron] Miscellaneous Control


And it looks like there isnt an ipod recognized anywhere on the system bus at all.

---

### Post by |{urse on 2010-09-14
Well, today I set up an ad-hoc connection and am able to do what I needed to do. I am still lost on why my ipod touch isnt autodetected. I'll still keep checking back, hopefully someone can enlighten me here.

---

### Post by |{urse on 2010-09-18
bump

---

### Post by |{urse on 2010-10-01
One week since my last bump and still no love. Anyone else?

---

### Post by someitalian123 on 2010-10-02
I think that the plug and play out of the box support for ipod touch in ubuntu is just for gnome. I don't think ipod touch is supported by solid__. If you need to access the filesystem have you tried mounting it in the terminal.

---

### Post by jdsmofo on 2010-10-03
No sign of any connection to my iPhone either.

---

### Post by |{urse on 2010-10-11
Yes, I've tried (again and again) to mount it via term. I'm thinking you are correct about it only being recognized in gnome ubuntu and not kubuntu. Kind of irritating, too bad that isn't clearly specified somewhere, if that's the case.

---

