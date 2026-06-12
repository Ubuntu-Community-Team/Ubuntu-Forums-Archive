---
title: "How to mount external HD partitions"
date: 2006-06-28
forum: General Help
---

### Post by CrossGT6 on 2006-06-28
Ok I have a small problem. 

I have an external HD that was in my last laptop. Its bigger then the one in my new laptop so I want to pull the data off it onto the smaller HD and then swap them. 

Now the External Drive was running Fedora Core 5 i386. My new laptop is PPC Ubuntu but the drive still has OS X Tiger on it. 

What I need to do is mount the External drive. It has two partitions one mounts right away and its called /boot but I do not know how to mount the other partition. 

Then I need to transfer everything to the other HD inside the laptop currently (I am running off the live cd right now) so i was going to format it fat32 since all os's can read it and I can continue to use it as an external drive. I think I know how to do that but if not I will ask for help. 

So hopefully I made it clear what I need lol. Thanks!

---

### Post by kzutter on 2006-06-28
This first thing to do is to identify the name of the device that linux has given to the external drive. You do not give any details as to the drive interface - firewire, usb, etc. - this info may help. Looks like the live cd sees the drive and mounts one of the  partitions (/boot). This is probably the first partition on the drive. If it had linux on it before, there are probably 3 or more partitions (/, /boot, and swap) and they may be primary or extended partitions.

Run this command to get a list of disk devices and their partitions:
```
sudo fdisk -l
```
Once you find the partition you want to mount (lets assume its sda2 for purposes of discussion), create a mount point for it.
```
sudo mkdir /mypart
```
And give it world read/write for simplicity
```
sudo chmod 777 /mypart
```
Then try to mount it
```
sudo mount sda2 /mypart
```
You may have to tell mount the type of filesystem if it cannot figure it out on its own.

Good luck:grin:

---

### Post by CrossGT6 on 2006-06-28
Ok when I do the fdisk it does not even show the /boot partition. 

I see the internal Hard Drive but nothing else that I think is the external drive because it says apple HFS and partitions. 

Sorry on not saying what I am using to connect it. I can use firewire or usb. I am currently using usb. 

Hope this helps! Thanks

---

### Post by CrossGT6 on 2006-06-28
Ok I  decided to use the install command and find out what the format of the other partition is....

It says unknown...

However it is 
/dev/sdb2

flags are:
lvm

So I am not sure what to think yet, what format would it be?

---

### Post by kzutter on 2006-06-28
Looks like Fedora set it up as a LVM - Logical Volume Manager
This is not the format however. I do not know what what Fedora's default fstype is at this time, probably ext3, but not sure.
LVM allows one to combine many physical partitions into one logical volume - cool for making a large virtual disk disk out of many smaller ones, but in this case it is presenting problems.
This is getting too far out of my league - I am not familiar with neither Fedora nor PPC.
Maybe a Fedora group could help you.

I suggest your next step is to bone up on LVM and how Fedora implements it.

Can you boot the Fedora OS on this drive. Then you could copy the files to a differnt drive or burn them to a cd/dvd.

I am sorry I cannot be of more help.

Good Luck,
Ken

---

### Post by CrossGT6 on 2006-06-29
Its ok I decided the same thing. I came to the same conclusion and the fedora forum is horrible they hardly ever answer hard questions. 

Its the main reason I really enjoy it here. 

I am downloading the FC5 discs now and I will just create a fat32 parition on the drive with only the size needed for fedora and hopefully be able to move everything to the fat32 partition. Hopefully I will have enough free space. 

From there I will load the 60gig into the laptop and install the os on it and transfer everything with the 40 in the external and hopefully be done with fedora... for good this time.

---

### Post by machia on 2006-07-04
I FOUND THE SOLUTION: **"sudo modprobe -r ehci_hcd" **
[here]("http://ubuntuforums.org/showthread.php?t=48126&highlight=ipod+mount+problem")


I have the same problem and i haven't got my usb ext-hd (300gb ext3) to work also. I used ultimate boot cd and set my ext-hd as ext3.

My setup. 2 drives hda&hdb and my usb ext-hd, cdrw&dvdrw-drives. hda contains the filesystem and hdb is just a data-folder. I have usb-mouse+keyboard+game pad. Using dapper-i386.

I used the "sudo fdisk- l" command and it shows the following 

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3852    30941158+   7  HPFS/NTFS
/dev/hda2           13286       14593    10506510    c  W95 FAT32 (LBA)
/dev/hda3            3859       13285    75722377+   5  Extended
/dev/hda5            3860        3990     1052257+  82  Linux swap / Solaris
/dev/hda6            3991        5942    15679408+  83  Linux
/dev/hda7            5943       13285    58982616   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24320   195350368+  83  Linux
```

So no ext-usb drive :(

My /dev-folder contains the following:
```
acpi       ptya4  ptyp8  ptyuc  ram0        tty60  ttyed   ttyS35  ttyw5
adsp       ptya5  ptyp9  ptyud  ram1        tty61  ttyee   ttyS36  ttyw6
agpgart    ptya6  ptypa  ptyue  ram10       tty62  ttyef   ttyS37  ttyw7
audio      ptya7  ptypb  ptyuf  ram11       tty63  ttyp0   ttyS38  ttyw8
bus        ptya8  ptypc  ptyv0  ram12       tty7   ttyp1   ttyS39  ttyw9
cdrom      ptya9  ptypd  ptyv1  ram13       tty8   ttyp2   ttys4   ttywa
cdrw       ptyaa  ptype  ptyv2  ram14       tty9   ttyp3   ttyS4   ttywb
console    ptyab  ptypf  ptyv3  ram15       ttya0  ttyp4   ttyS40  ttywc
core       ptyac  ptyq0  ptyv4  ram2        ttya1  ttyp5   ttyS41  ttywd
disk       ptyad  ptyq1  ptyv5  ram3        ttya2  ttyp6   ttyS42  ttywe
dmmidi1    ptyae  ptyq2  ptyv6  ram4        ttya3  ttyp7   ttyS43  ttywf
dsp        ptyaf  ptyq3  ptyv7  ram5        ttya4  ttyp8   ttyS44  ttyx0
dvd        ptyb0  ptyq4  ptyv8  ram6        ttya5  ttyp9   ttyS45  ttyx1
dvdrw      ptyb1  ptyq5  ptyv9  ram7        ttya6  ttypa   ttyS46  ttyx2
evms       ptyb2  ptyq6  ptyva  ram8        ttya7  ttypb   ttyS47  ttyx3
fb0        ptyb3  ptyq7  ptyvb  ram9        ttya8  ttypc   ttys5   ttyx4
fd         ptyb4  ptyq8  ptyvc  random      ttya9  ttypd   ttyS5   ttyx5
fd0        ptyb5  ptyq9  ptyvd  rtc         ttyaa  ttype   ttys6   ttyx6
full       ptyb6  ptyqa  ptyve  sequencer   ttyab  ttypf   ttyS6   ttyx7
hda        ptyb7  ptyqb  ptyvf  sequencer2  ttyac  ttyq0   ttys7   ttyx8
hda1       ptyb8  ptyqc  ptyw0  shm         ttyad  ttyq1   ttyS7   ttyx9
hda2       ptyb9  ptyqd  ptyw1  snd         ttyae  ttyq2   ttys8   ttyxa
hda3       ptyba  ptyqe  ptyw2  sndstat     ttyaf  ttyq3   ttyS8   ttyxb
hda5       ptybb  ptyqf  ptyw3  stderr      ttyb0  ttyq4   ttys9   ttyxc
hda6       ptybc  ptyr0  ptyw4  stdin       ttyb1  ttyq5   ttyS9   ttyxd
hda7       ptybd  ptyr1  ptyw5  stdout      ttyb2  ttyq6   ttysa   ttyxe
hdb        ptybe  ptyr2  ptyw6  tty         ttyb3  ttyq7   ttysb   ttyxf
hdb1       ptybf  ptyr3  ptyw7  tty0        ttyb4  ttyq8   ttysc   ttyy0
hdc        ptyc0  ptyr4  ptyw8  tty1        ttyb5  ttyq9   ttysd   ttyy1
hdd        ptyc1  ptyr5  ptyw9  tty10       ttyb6  ttyqa   ttyse   ttyy2
hpet       ptyc2  ptyr6  ptywa  tty11       ttyb7  ttyqb   ttysf   ttyy3
initctl    ptyc3  ptyr7  ptywb  tty12       ttyb8  ttyqc   ttyt0   ttyy4
input      ptyc4  ptyr8  ptywc  tty13       ttyb9  ttyqd   ttyt1   ttyy5
kmem       ptyc5  ptyr9  ptywd  tty14       ttyba  ttyqe   ttyt2   ttyy6
kmsg       ptyc6  ptyra  ptywe  tty15       ttybb  ttyqf   ttyt3   ttyy7
log        ptyc7  ptyrb  ptywf  tty16       ttybc  ttyr0   ttyt4   ttyy8
loop       ptyc8  ptyrc  ptyx0  tty17       ttybd  ttyr1   ttyt5   ttyy9
lp0        ptyc9  ptyrd  ptyx1  tty18       ttybe  ttyr2   ttyt6   ttyya
lvm        ptyca  ptyre  ptyx2  tty19       ttybf  ttyr3   ttyt7   ttyyb
MAKEDEV    ptycb  ptyrf  ptyx3  tty2        ttyc0  ttyr4   ttyt8   ttyyc
mapper     ptycc  ptys0  ptyx4  tty20       ttyc1  ttyr5   ttyt9   ttyyd
md0        ptycd  ptys1  ptyx5  tty21       ttyc2  ttyr6   ttyta   ttyye
md1        ptyce  ptys2  ptyx6  tty22       ttyc3  ttyr7   ttytb   ttyyf
md10       ptycf  ptys3  ptyx7  tty23       ttyc4  ttyr8   ttytc   ttyz0
md11       ptyd0  ptys4  ptyx8  tty24       ttyc5  ttyr9   ttytd   ttyz1
md12       ptyd1  ptys5  ptyx9  tty25       ttyc6  ttyra   ttyte   ttyz2
md13       ptyd2  ptys6  ptyxa  tty26       ttyc7  ttyrb   ttytf   ttyz3
md14       ptyd3  ptys7  ptyxb  tty27       ttyc8  ttyrc   ttyu0   ttyz4
md15       ptyd4  ptys8  ptyxc  tty28       ttyc9  ttyrd   ttyu1   ttyz5
md16       ptyd5  ptys9  ptyxd  tty29       ttyca  ttyre   ttyu2   ttyz6
md17       ptyd6  ptysa  ptyxe  tty3        ttycb  ttyrf   ttyu3   ttyz7
md18       ptyd7  ptysb  ptyxf  tty30       ttycc  ttys0   ttyu4   ttyz8
md19       ptyd8  ptysc  ptyy0  tty31       ttycd  ttyS0   ttyu5   ttyz9
md2        ptyd9  ptysd  ptyy1  tty32       ttyce  ttys1   ttyu6   ttyza
md20       ptyda  ptyse  ptyy2  tty33       ttycf  ttyS1   ttyu7   ttyzb
md21       ptydb  ptysf  ptyy3  tty34       ttyd0  ttyS10  ttyu8   ttyzc
md22       ptydc  ptyt0  ptyy4  tty35       ttyd1  ttyS11  ttyu9   ttyzd
md23       ptydd  ptyt1  ptyy5  tty36       ttyd2  ttyS12  ttyua   ttyze
md24       ptyde  ptyt2  ptyy6  tty37       ttyd3  ttyS13  ttyub   ttyzf
md3        ptydf  ptyt3  ptyy7  tty38       ttyd4  ttyS14  ttyuc   urandom
md4        ptye0  ptyt4  ptyy8  tty39       ttyd5  ttyS15  ttyud   vcs
md5        ptye1  ptyt5  ptyy9  tty4        ttyd6  ttyS16  ttyue   vcs1
md6        ptye2  ptyt6  ptyya  tty40       ttyd7  ttyS17  ttyuf   vcs2
md7        ptye3  ptyt7  ptyyb  tty41       ttyd8  ttyS18  ttyv0   vcs3
md8        ptye4  ptyt8  ptyyc  tty42       ttyd9  ttyS19  ttyv1   vcs4
md9        ptye5  ptyt9  ptyyd  tty43       ttyda  ttys2   ttyv2   vcs5
mem        ptye6  ptyta  ptyye  tty44       ttydb  ttyS2   ttyv3   vcs6
midi1      ptye7  ptytb  ptyyf  tty45       ttydc  ttyS20  ttyv4   vcs7
mixer      ptye8  ptytc  ptyz0  tty46       ttydd  ttyS21  ttyv5   vcs8
mixer1     ptye9  ptytd  ptyz1  tty47       ttyde  ttyS22  ttyv6   vcsa
net        ptyea  ptyte  ptyz2  tty48       ttydf  ttyS23  ttyv7   vcsa1
null       ptyeb  ptytf  ptyz3  tty49       ttye0  ttyS24  ttyv8   vcsa2
nvidia0    ptyec  ptyu0  ptyz4  tty5        ttye1  ttyS25  ttyv9   vcsa3
nvidiactl  ptyed  ptyu1  ptyz5  tty50       ttye2  ttyS26  ttyva   vcsa4
parport0   ptyee  ptyu2  ptyz6  tty51       ttye3  ttyS27  ttyvb   vcsa5
port       ptyef  ptyu3  ptyz7  tty52       ttye4  ttyS28  ttyvc   vcsa6
ppp        ptyp0  ptyu4  ptyz8  tty53       ttye5  ttyS29  ttyvd   vcsa7
psaux      ptyp1  ptyu5  ptyz9  tty54       ttye6  ttys3   ttyve   vcsa8
ptmx       ptyp2  ptyu6  ptyza  tty55       ttye7  ttyS3   ttyvf   vmmon
pts        ptyp3  ptyu7  ptyzb  tty56       ttye8  ttyS30  ttyw0   vmnet0
ptya0      ptyp4  ptyu8  ptyzc  tty57       ttye9  ttyS31  ttyw1   xconsole
ptya1      ptyp5  ptyu9  ptyzd  tty58       ttyea  ttyS32  ttyw2   zero
ptya2      ptyp6  ptyua  ptyze  tty59       ttyeb  ttyS33  ttyw3
ptya3      ptyp7  ptyub  ptyzf  tty6        ttyec  ttyS34  ttyw4
```

"lsusb" gives the following:

```
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 005: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 001 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

I was just wondering that could there be some problem with the usb-ports? But then why does the partition magic (booting from ultimate-cd) see it and can handle it without problems? I tried 3 or more partition tools and they see it normally.. Anyone got ideas?

---

