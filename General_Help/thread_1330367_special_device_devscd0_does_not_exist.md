---
title: "special device /dev/scd0 does not exist"
date: 2009-11-18
forum: General Help
---

### Post by rondelli on 2009-11-18
Hey there!
I`m facing a huge problem here guys.
I`ve installed ubuntu 9.10 on my laptop, I`ve created a partition with gpart and now have an exceptional dual boot with xp sp2. Why? Because I`m a developer and if I browse the linux community there aren`t sufficient tools that match the windows ones, but this isn`t the point here. 

My cd dosen`t mount. I really love to learn linux but sorry guys I really need my cdrom.

K here`s what I`ve done, and yes I have thoroughly browsed the forum for simmilar topics.


1) if I try: sudo mount -t iso9660 /dev/hda /media/cdrom0
it outputs to:
mount: special device /dev/hda does not exist;
the same if I try with /dev/scd0;
2)if I try to use: lshal | grep CD:
The ordinateur dosen`t find the device.
3)If I try to use: sudo gedit /etc/fstab:
I have the line: /dev/scd0  /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
I have tried commenting out the line booting and rebooting;
4)If I use lsusb:

BUS 003 Device 001: ID 1d6b: 0001 Linux foundation 1.1 root hub
BUS 002 Device 001: ID 1d6b: 0001 Linux foundation 1.1 root hub
BUS 005 Device 001: ID 1d6b: 0001 Linux foundation 1.1 root hub
BUS 001 Device 002: ID 0c45: 62c0 Microdia Sonix USB 2.0 Camera
BUS 001 Device 001: ID 1d6b: 0002 Linux foundation 2.0 root hub
BUS 004 Device 001: ID 1d6b: 0001 Linux foundation 1.1 root hub

care to mention that my dvdrom is not an external drive

5)if I boot with the Live CD it works, If I boot with any other cd, format same message, also it is available in win xp.

6)I have tried to open the /boot/grub/menu.lst --> I couldn`t find any file with the name menu.lst
also used the command: ls /boot/grub/ | grep menu
I tried to open this file so I could add the noapic option at the end of the line 
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash

7)I have tried to replace the line /dev/scd0 in /etc/fstab with: hdc and with hda
Dosen`t work.

8)cdrecord --scanbus outputs:
wodim: No such file or directory;
Cannot open SCSI driver!;

9)running : ls -al /media 
OUTPUTS:

drwxr -xr - x 3 root root 4096 2099-11-16 02:42
drwxr -xr - x 21 root root 4096 2009-11-16 02:20
lrwxrwxrwx 1 root root      6 2009-11-16 01:53 cdrom -> cdrom0
drwxr -xr - x 2 root root 4096 2009-11-16 01:53 cdrom0

10)my primary HDD is /dev/sda

11)In my media directory there is a cdrom0 subdirectory

12)later edit: sudo gedit /etc/fstab
edited the line "udf, iso9660" with auto: same message

Please HELP

---

### Post by fahadsadah on 2009-11-18
It works in the LiveCD?

If so, please post the output of
```
sudo mount
```

---

### Post by falconindy on 2009-11-18
You're looking in the wrong places. Check the output of:
```
sudo lshw -c disk
```
The liveCD will load a more robust set of kernel modules. It's possible that a different module is claiming your drive on your install and thus naming it differently than what you expect. I encountered this on my Arch install when I was paring down my boot image.

Semi-unrelated: What tools are you using on Windows that you find aren't matched on Linux? No offense, but I suspect you haven't looked hard enough.

---

### Post by rondelli on 2009-11-18
> **fahadsadah said:**
> It works in the LiveCD?

If so, please post the output of
```
sudo mount
```

   /dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gabriel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gabriel)
/dev/sdb1 on /media/C863-99B2 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

  
> You're looking in the wrong places. Check the output of:
 	Code:
 	sudo lshw -c disk 
The liveCD will load a more robust set of kernel modules. It's possible that a different module is claiming your drive on your install and thus naming it differently than what you expect. I encountered this on my Arch install when I was paring down my boot image.

Semi-unrelated: What tools are you using on Windows that you find aren't matched on Linux? No offense, but I suspect you haven't looked hard enough.

   *-disk
       description: ATA Disk
       product: FUJITSU MHW2080B
       vendor: Fujitsu
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0000
       serial: K101T7A2ES9L
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=052a0529

  
Unrelated: Let`s say Adobe Dreamweaver CS3.

---

### Post by rondelli on 2009-11-19
So anyone with ideas on how to fix this?
I found that there are numerous others that share my situation so there must be an official answer or something of the sorts.
Come on guys!!! It`s the 9.10 release of a well-known Linux system for beginners.

---

### Post by rondelli on 2009-11-19
Ok so I found a partial solution
If I boot with the option noapic acpi=off, it even starts with the cd drive on the desktop.
I tried editing under root with
sudo gedit /boot/ggrub/grub.cfg
to add at the end of the line noapic acpi=off, but i still get an error message that the disk is read only so I can`t save the file at it`s current location.
Any ideas on how to solve this?

---

### Post by falconindy on 2009-11-19
> *-disk
description: ATA Disk
product: FUJITSU MHW2080B
vendor: Fujitsu
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: 0000
serial: K101T7A2ES9L
size: 74GiB (80GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=052a0529
Unless you've skipped a section of the output, lshw says you don't have a dvd drive.

> **rondelli said:**
> Ok so I found a partial solution
If I boot with the option noapic acpi=off, it even starts with the cd drive on the desktop.
Hrm, that seems like a bad tradeoff just to get cd-rom access.


> **rondelli said:**
> I tried editing under root with
sudo gedit /boot/ggrub/grub.cfg
to add at the end of the line noapic acpi=off, but i still get an error message that the disk is read only so I can`t save the file at it`s current location.
Any ideas on how to solve this?
grub.cfg isn't meant to be directly edited, thanks to Canonical's suite of maintenance scripts. If you do `ls -l /boot/grub/grub.cfg` you'll see its "-r---------". You'll need to edit the appropriate header file under /etc/grub.d/ and then re-run update-grub.

Post the output of `lsmod` and `lshw -c disk` when your cd rom shows up.

---

### Post by rondelli on 2009-11-19
to lsmod

   Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52544  1 
isofs                  31620  1 
joydev                 10272  0 
uvcvideo               59080  0 
binfmt_misc             8356  1 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
psmouse                56180  0 
serio_raw               5280  0 
ppdev                   6688  0 
snd_hda_codec_si3054     4636  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
arc4                    1660  2 
ecb                     2524  2 
iwl3945                77212  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
pcmcia                 36808  0 
iwlcore               112508  1 iwl3945
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181236  2 iwl3945,iwlcore
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  2 iwl3945,iwlcore
lp                      8964  0 
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24200  1 
soundcore               7264  1 snd
parport                35340  2 ppdev,lp
rsrc_nonstatic         11644  1 yenta_socket
tifm_7xx1               5372  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 iwl3945,iwlcore,mac80211
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core               7832  1 tifm_7xx1
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  0 
agpgart                34988  1 intel_agp

  
to lshw -c disk

     *-disk
       description: ATA Disk
       product: FUJITSU MHW2080B
       vendor: Fujitsu
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0000
       serial: K101T7A2ES9L
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=052a0529
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SN-S082H
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 124MiB (130MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=42116736

  
> grub.cfg isn't meant to be directly edited, thanks to Canonical's suite of maintenance scripts.The headers in /etc/grub.d are just too complicated for poor lil me so instead of using **sudo gedit** I used **sudo nano /boot/grub/grub.cfg **and WORKED :D
Why do you say it`s a bad tradeoff? If you can help me I will remain in your debt :).

---

### Post by falconindy on 2009-11-19
Ok, sweet. Good news, bad news, and semi-unrelated news.

Semi-unrelated: Ubuntu doesn't have access to some modules I assumed it does. 

Good news: acpi=off isn't as bad as I thought it was and I think it should suffice.

Bad news: I'm going to make you edit the files in /etc/grub.d. If you don't, you'll end up having to edit grub.cfg every time update-grub is run, and you don't want to have to do that. Better to just make the change permanent. Open "/etc/grub.d/10_linux" and find the function linux_entry() -- it should be around line 56. About 15 lines below that, you'll see a line that looks like this:
```
    linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion}     ro $2
```
Add your options to the end of that line, save it, and run `sudo update-grub`. Now, when you go into /boot/grub/grub.cfg, you should see your options tacked onto to boot entry for Karmic.

---

### Post by rondelli on 2009-11-19
> **falconindy said:**
> Ok, sweet. Good news, bad news, and semi-unrelated news.


Bad news: I'm going to make you edit the files in /etc/grub.d. If you don't, you'll end up having to edit grub.cfg every time update-grub is run, and you don't want to have to do that. Better to just make the change permanent. Open "/etc/grub.d/10_linux" and find the function linux_entry() -- it should be around line 56. About 15 lines below that, you'll see a line that looks like this:
```
    linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion}     ro $2
```Add your options to the end of that line, save it, and run `sudo update-grub`. Now, when you go into /boot/grub/grub.cfg, you should see your options tacked onto to boot entry for Karmic.

Good...goood :popcorn: I like editing code. The thing is I saw that line when I skimmed 10_linux, but didn`t want to change something without being absolutely certain. Thanks a mile! So please explain in layman terms what this acpi option does, in case I decide to abandon the cd option in favour of a USB one. 
How will acpi=off will affect me on the long run?

If you`ll answer that I`ll promise to send you a home-made Ubuntu blend coffee :)

---

### Post by falconindy on 2009-11-19
ACPI is your power management. Disabling it **can** lead to undesired effects, particularly on desktops, but laptops use a more advanced type of power management called APM. Given that I haven't owned a laptop in the past decade, I wasn't aware of APM. I assumed that disabling ACPI could cut your battery life in half, cause half your devices to stop working, and possibly kick your dog. Don't worry, I think your dog is safe. Run it for a few days and make sure that nothing else is acting funky, though.

I like my coffee light, and Arch flavored. ;)

---

### Post by QLee on 2009-11-19
> **falconindy said:**
> ACPI is your power management. Disabling it **can** lead to undesired effects, particularly on desktops, but laptops use a more advanced type of power management called APM. Given that I haven't owned a laptop in the past decade, I wasn't aware of APM. I assumed that disabling ACPI could cut your battery life in half, cause half your devices to stop working, and possibly kick your dog. Don't worry, I think your dog is safe. Run it for a few days and make sure that nothing else is acting funky, though.


Huh? APM is the old method, ACPI is the newer.

---

### Post by falconindy on 2009-11-19
> **QLee said:**
> Huh? APM is the old method, ACPI is the newer.
Hmm, so it is. Keep an eye on your dog.

---

### Post by rondelli on 2009-11-20
Thanks. How did you know I own a dog? 
I`m willin to lookup Arch in order to solve that mistery ;)

---

### Post by rondelli on 2009-11-22
First consequence on ACPI=OFF. No battery management, I`ve lost the main Battery Icon.
Do you think I should submit a Bug Report?

---

### Post by rondelli on 2009-11-22
Now my DVD-Rom in Windows XP does not work either.
So it`s not about that my unit just crashed after installation cause the Live CD boots well and if I add the line noapic acpi=off the cd starts but with limited support for batery management on my laptop in Ubuntu.
My BIOS settings are the same, cause I reversed to the default ones and they remain the same, either way my POST screen and boot diagnostic tool sees my DVD-ROM.
So what`s the catch?

---

### Post by JeanB on 2009-12-02
Hi I have the same problem than you, I guess:

"FATAL: module CDROM not found"[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

Did you finally find a solution?
Was it a catch?

---

### Post by sparty_xubunter on 2009-12-03
I have the same problem in 9.10.  I'm running it on a desktop though.  DVD/CD-ROM doesn't read anything. Worked fine in 9.04 from what I remember.

Like Rondelli I've scoured the forum and have yet to find a solution beyond the proposed ACPI option.  Which seems sub-optimal

Any help?

---

### Post by JeanB on 2009-12-04
up

---

### Post by rondelli on 2009-12-16
guys I`m gonna unninstall my ubuntu version 9.10.
I want my cdrom back.

---

### Post by JeanB on 2009-12-19
YEAPAAA!!! I've found "my" solution. Hoping that it may be useful for many others.
I've just changed my IDE writer for a SATA one....and ALLELUIA! After some frustrating months and multiples interventions in many forums in three languages... YES!!!I've got it!
It is something very easy to do in a PC( it's the first time I opened the tower, so if I did it...) for an acceptable price (around 22 Euros)
In a laptop...?
I remind that the symptoms were ; a driver recognized but without any media found (audio, video, data. NOTHING!)

Merry christmas

Jean-Pierre

---

### Post by JeanB on 2009-12-19
YEAPAAA!!! I've found "my" solution. Hoping that it may be useful for many others.
I've just changed my IDE writer for a SATA one....and ALLELUIA! After some frustrating months and multiples interventions in many forums in three languages... YES!!!I've got it!
It is something very easy to do in a PC( it's the first time I opened the tower, so if I did it...) for an acceptable price (around 22 Euros)
In a laptop...?
I remind that the symptoms were ; a writer recognized but without any media found (audio, video, data. NOTHING!)

Merry christmas

Jean-Pierre

---

### Post by sportscliche on 2010-02-20
Like many others it seems, I have this problem in Ubuntu 9.10.  Some additional information on my situation that may be of use:  I can choose to run Kubuntu 9.10 or Ubuntu 9.10 from my XP host using VMWare Player.  Only Ubuntu fails to mount the CD/ROM.  The relevant line in /etc/fstab looks identical in both Linux distros, so the problem must be in Ubuntu.  Also, I had a difficult time getting sound in Ubuntu (now solved thanks to these forums).  All the peripherals came up fine on the Kubuntu install.  I'm a Linux newbie and much prefer the Ubuntu interface, but not having access to the CD/ROM is a deal-breaker.

---

### Post by sportscliche on 2010-02-21
My problem turned out to be with the VMWare Player interface, not Ubuntu or Grub.  If you are running Ubuntu as a guest and having problems, I'd suggest carefully checking the .vmx file.  I did a direct comparison of the .vmx files for Kubuntu 9.10 (which worked) and Ubuntu 9.10 (which was having difficulty).  You do this on the host OS, which in my case is XP.  Editing the Ubuntu .vmx to align with the working one eventually enabled the CDROM in Ubuntu and got me going.  Also it's probably a good idea to have VMWare agent/tools installed inside Ubuntu.

---

### Post by Khorre on 2010-03-14
Same issue, it'll appear sometimes, other times it won't. I don't know what exactly the issue is, my brother who introduced me to Linux just suggested I Google the error message, and that led me here.

I am a Mint user, if that has any effect.

---

### Post by kyreks4 on 2010-03-20
I am having the same exact problem, with the exception that I have no idea how to fix it, even after reading this thread several times... :(  somebody please help! I am a noob with linux, (but am learning quickly), so somebody, anybody please help!

(using Ubuntu: Karmic Koala)

---

### Post by soltanis on 2010-03-20
Wow, I just realized my CD drive is acting funky as well.

What the hell did the Ubuntu people do? CD support has been working since like, before the 2.2 kernels.

---

### Post by kyreks4 on 2010-04-17
P.F.M.!!! (pure freakin magic)

Ubuntu must have fixed itself!!!

one day i ran a cd by mistake forgetting that my drive was not working and it just decided to work....

FINALLY a positive "ghost in the machine":lolflag:

---

### Post by Khorre on 2010-05-10
old moldy bump. I got it working for awhile... but just recently it did this error again, and I have no recollection of how I fixed it the first time (all I remember was that it took a long frustrating search)
anyone have suggestions for this problem?

---

