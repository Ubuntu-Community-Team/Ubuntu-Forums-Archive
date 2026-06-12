---
title: "Ghost CD"
date: 2009-07-06
forum: General Help
---

### Post by DiegoTe5 on 2009-07-06
Hi all,
I got a problem with my cd reader: there is no CD inside, but there is a CD icon called "Bluebirds" on my desktop, as if it were a CD. I can "eject" it from the contextual menu and the cd case opens and the icon is gone; i close it again and it appears once more. When i introduce a CD, it works well, though, and the icon isn't there, just to reappear when the cd is ejected.
After a bit of searching:
```
Blurebirds Drag & Burn is disc writing software. It is included in the drives memory instead of being on a separate disc. Only certain drives have it (refer to the specs).
```
[[http://lgknowledgebase.com/kb/index.php?View=entry&EntryID=6271]("http://lgknowledgebase.com/kb/index.php?View=entry&EntryID=6271")]
I have a LG cd reader, so that must be it. How do i fix it/get it working all right?

Thanks for the help.

---

### Post by Jebtrix on 2009-07-06
Without a real CD inside and the 'ghost' CD icon on the desktop goto terminal and type:

```
lshal
```

Your going to see a bunch of stuff, look for something like this:
```

udi = '/org/freedesktop/Hal/devices/volume_label_VMware_Tools'
  block.device = '/dev/sr0'  (string)
  block.is_volume = true  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_VMware_IDE_CDR10'  (string)

....

  volume.disc.type = 'dvd_rom'  (string)
  volume.label = 'VMware Tools'  (string)
```

The "volume.label =" is the name given to the icon you see automounted on your desktop. What I need to know from your comp is what it has for "block.device =" parameter. So with no real cd, does block.device = '/dev/sr0'? When you have a real CD does the ghost CD still appear on desktop? If it is, does the parameter "block.device = '/dev/sr0'" still point to the 'ghost' disc? or does it change?

---

### Post by Jebtrix on 2009-07-06
Easier yet do:

```
lshal > ~/Desktop/devicelist.txt
gedit ~/Desktop/devicelist.txt
```

Then search for BlueBirds, that will narrow the search to the right device entry..

---

### Post by Jebtrix on 2009-07-06
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

<device>
<match key="volume.label" string="Bluebirds">
<merge key="volume.ignore" type="bool">true</merge>
</match>
</device>

</deviceinfo>

```

Open gedit, past that code into a new document.
Save to Desktop as diebluebirds.fdi
Open Terminal do:

```
sudo mv ~/Desktop/diebluebirds.fdi /etc/hal/fdi/policy
sudo /etc/init.d/hal restart
```

You may have to restart machine, I'm not sure what restarting hal will do when its already automounted on your desktop.

Without more info from you, this will ignore anything with Bluebirds as a volume label. Its case sensitive so make sure it is Bluebirds and not bluebirds. Most likely nothing else will ever have this name, but the best solution would be narrow the filter down with more than just the volume label.

---

### Post by DiegoTe5 on 2009-07-06
> What I need to know from your comp is what it has for "block.device =" parameter. So with no real cd, does block.device = '/dev/sr0'?
Yes
> When you have a real CD does the ghost CD still appear on desktop?
No



> Without more info from you, this will ignore anything with Bluebirds as a volume label. Its case sensitive so make sure it is Bluebirds and not bluebirds. Most likely nothing else will ever have this name, but the best solution would be narrow the filter down with more than just the volume label.
That means that there is no other way than to explicitly ignore anything called Blubirds? :-?

---

### Post by Jebtrix on 2009-07-15
No thats not the only way. You could match more than just one property. You would have to post your **lshal** output with an actual disc in and without for me to see if there is more properties that make the rule more unique.

---

### Post by caue.rego on 2009-07-31
related: [http://ubuntuforums.org/showthread.php?p=7713016#post7713016](http://ubuntuforums.org/showthread.php?p=7713016#post7713016)

I'll post **lshal** for ya, meanwhile I'll research about that hal guy.

I can also add one thing to you: the behavior is the exact same on windows. The bluebirds appears as a wandering ghost while no media is inserted on the drive. Quite annoying "added feature" from LG, but I guess it only disturbs ubuntu users and odd glassed people as myself (although I don't use 'em).

Plus, I've tried mounting it as RW so I could freaking delete the files, but with no success... Here's what oddly happened:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123122&stc=1&d=1249080691[/IMG]

And next there are the parts of your interest on lshal's.

mounted (as on the picture) lshal
```
udi = '/org/freedesktop/Hal/devices/volume_label_Bluebirds'
  block.device = '/dev/sr0'  (string)
  block.is_volume = true  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50'  (string)
  info.capabilities = {'volume.disc', 'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50'  (string)
  info.product = 'Bluebirds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_label_Bluebirds'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0/fakevolume'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 2048  (0x800)  (int)
  volume.disc.capacity = 6293504  (0x600800)  (uint64)
  volume.disc.has_audio = false  (bool)
  volume.disc.has_data = true  (bool)
  volume.disc.is_appendable = false  (bool)
  volume.disc.is_blank = false  (bool)
  volume.disc.is_blurayvideo = false  (bool)
  volume.disc.is_rewritable = false  (bool)
  volume.disc.is_svcd = false  (bool)
  volume.disc.is_vcd = false  (bool)
  volume.disc.is_videodvd = false  (bool)
  volume.disc.type = 'cd_rom'  (string)
  volume.fstype = 'iso9660'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = true  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = true  (bool)
  volume.is_partition = false  (bool)
  volume.label = 'Bluebirds'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'uid=', 'mode=', 'iocharset='} (string list)
  volume.mount_point = '/media/cdrom0'  (string)
  volume.num_blocks = 12292  (0x3004)  (uint64)
  volume.size = 6293504  (0x600800)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = ''  (string)

```

umounted lshal
```
udi = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50'
  access_control.file = '/dev/sr0'  (string)
  access_control.type = 'cdrom'  (string)
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom', 'access_control'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'DVDRAM GH22NS50'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50'  (string)
  info.vendor = 'HL-DT-ST'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 8467  (0x2113)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8468  (0x2114)  (int)
  storage.cdrom.write_speeds = {'8468', '8467', '7057', '7056', '5646', '5645', '4235', '4234', '2822', '1411', '706'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'TN00'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'DVDRAM GH22NS50'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.media_size = 6293504  (0x600800)  (uint64)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'HL-DT-ST'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_0_scsi_device_lun0_scsi_generic'
  access_control.file = '/dev/sg1'  (string)
  access_control.type = 'cdrom'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'scsi_generic', 'access_control'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

```

I've only found difference on read_speed (from 8467 to 1764), partitioning_scheme (from existant to not there) and media_available (from false to true).

---

### Post by caue.rego on 2009-07-31
> **Jebtrix said:**
> ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

<device>
<match key="volume.label" string="Bluebirds">
<merge key="volume.ignore" type="bool">true</merge>
</match>
</device>

</deviceinfo>

```

Open gedit, past that code into a new document.
Save to Desktop as diebluebirds.fdi
Open Terminal do:

```
sudo mv ~/Desktop/diebluebirds.fdi /etc/hal/fdi/policy
sudo /etc/init.d/hal restart
```

You may have to restart machine, I'm not sure what restarting hal will do when its already automounted on your desktop.

Without more info from you, this will ignore anything with Bluebirds as a volume label. Its case sensitive so make sure it is Bluebirds and not bluebirds. Most likely nothing else will ever have this name, but the best solution would be narrow the filter down with more than just the volume label.

By the way, you could use

```
sudo service hal restart
```

**And your patch worked!** Both with the service restart, and after rebooting my machine. It's ugly as hell (developer-wise), but at least bluebirds is gone! :D

Have fun with the lshal, tho. ;)

---

### Post by Krallus on 2009-09-04
Assuming you have the LG GH22NS50, you can remove that stupid Bluebirds thing using the tool here:

[http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50](http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50)

Also discussed here:

[http://www.msfn.org/board/lg-gh22ns50-bluebirds-removal-tool-t135300-pid-881021-page-40.html&#entry881021](http://www.msfn.org/board/lg-gh22ns50-bluebirds-removal-tool-t135300-pid-881021-page-40.html&#entry881021)

---

### Post by caue.rego on 2009-09-09
> **Krallus said:**
> Assuming you have the LG GH22NS50, you can remove that stupid Bluebirds thing using the tool here:

[http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50](http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50)

Also discussed here:

[http://www.msfn.org/board/lg-gh22ns50-bluebirds-removal-tool-t135300-pid-881021-page-40.html&#entry881021](http://www.msfn.org/board/lg-gh22ns50-bluebirds-removal-tool-t135300-pid-881021-page-40.html&#entry881021)

thank you, finally LG took a step!

---

### Post by darkhelmetchris on 2010-10-27
I sincerely thank the participants in this forum for a great solution to the "LG Bluebirds problem".

This solution no longer works for Ubuntu 10.10.  From what I can tell, there no longer seems to be a hal service in Ubuntu 10.10 and so I am wondering... any ideas on how to apply a similar fix under Ubuntu 10.10?

---

### Post by Krallus on 2010-10-27
All you should have to do is upgrade the CD drive to the latest firmware: [http://www.lg.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50](http://www.lg.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50)

There's three listed, but if it were me, I'd do TN-03.  I can't remember the exact steps I used, but I likely booted to Windows (yes I still hang on to a Windows partition, though it is very rarely used) and installed the firmware from there.  You only have to run it on the drive once -- so you could even remove the drive and install it on a Windows machine in order to upgrade the firmware.  If you don't want to do it yourself, if you bring the drive into a shop or your local Staples, I'm sure they could update the firmware for you.

---

### Post by darkhelmetchris on 2010-10-28
tee hee.  I admit, that is one way, and I thank you for the response, Krallus.

However, I hesitate to remove the drive and flash it with someone's Windows (not that I wouldn't of course) but this is a Linux forum and I'm sure I'm not the only one to encounter this under some Linux distro.  So, I would like to see a pure 'nix solution - both for the experience and the spirit of sharing the option with others.  Also, I don't have any Windows installations here and disassembly of the workstation is undesirable due to the type of machine that it is.  It is an oil-cooled aquarium computer, so disassembly is, not just more difficult, but also kind of messy.  I will attach a pic to the post.

I was quite happy with the HAL blacklist, as it worked perfectly in the existing installation.  I expect there is a way to duplicate this with some form of blacklist - perhaps with an automounter blacklist or the new equivalent to HAL which I am as yet unfamiliar.

Anyone for a pure Linux option?

---

### Post by darkhelmetchris on 2011-01-04
Okay, this thread has been dead for a bit, and so I'm wondering if anyone knows how to:
"blacklist a volume by label" in Ubuntu 10.10 (the old HAL solution from previous Ubuntu version no longer works, as there is no HAL in this version)

Since most of my computer is submerged in white oil, taking the LG-Bluebirds drive out to flash in some other Windows machine is - really quite undesirable, so I have been living with the ghost CD always appearing.

Someone know how to blacklist a volume by label?

---

### Post by ischliky on 2011-02-20
I found 1 solution that worked great for me, however im not really sure how 'safe' it is so use at your own risk.

i read a few pages about this, some of which saying crossover would allow this to work, so i figured that wine should work as well.  however it was not really getting me anywhere.

then i decided that its quite possible i need to be running as root to have enough permissions to be able to flash the firmware.

long story short, this is what i did to fix it ( once again use at your own risk )  :

download TN01 - TN03 firmware, can find easily with google

open terminal

sudo su -                <- this is the part that really isnt normally a good idea

make sure CD is shut to start

wine /home/{your_login}/Desktop/GH22N....exe

once loaded, you can up eject the CD and hit update.  This shouldnt take but a few seconds and it should be all fixed and ready to go.


once again use this at your own risk, it worked great for me but i know that lots of people will say why doing the    sudo su -   is a bad idea.  however im not that great with wine so i wasnt sure how to get it to use a prefix that root had permissions for to load up wine.

feel free to update this with a safer way if you need, however this worked 100% for me, with a standard 10.10 ubuntu setup.

---

### Post by darkhelmetchris on 2012-08-02
Thanks for the info, [ischliky]("http://ubuntuforums.org/member.php?u=869666").  I tried your solution and didn't have much luck.  I can run wine, and applications in wine just fine.  But, for some reason, this solution didn't work for me; I tried several settings to address the drive, but got stuck each time.  The firmware update tool just hung and never updated the firmware in the drive, even after several tries with various settings.  Each time I ran it under wine, I waited nearly an hour to see some indication of activity, but it never progressed.  ...sadly.

In desperation, finally, I took the drive out of my aquarium, cleaned off the oil as best as I could (terrible mess, lol, but okay), plugged it into a friend's Windows box, and ran the firmware update tool.  It wasn't an Ubuntu/Linux solution, though.

I am still interested in finding out if anyone knows how to blacklist a volume by name in more recent versions of Ubuntu.  It would be handy to know, since there are a couple of USB volumes (not discs) that I insert that I wouldn't really like to appear until after I have performed other tasks with them.  The details are not really important, except to say that I don't want to turn of auto-mount completely because I do like it, most of the time.  If I had the ability to blacklist a volume by its name, that would make my life a little bit nicer when I am preparing certain volumes for use.

---

