---
title: "Lucid is driving me crazy- cannot mount external drives"
date: 2010-05-15
forum: General Help
---

### Post by GuiGuy on 2010-05-15
I have a number of HDD formatted to ext4 that I use from a esata docking station. Under karmic these worked fine and auto-mounting was reasonably reliable.

No, under lucid <grrrr> I get "You are not privileged to mount volume <volumename>"

I have checked my user account, which is flagged to mount removable devices etc. My user account is administrator.

I can, of course sudo mount, but that's inconvenient given it's a removable drive.

How can I change the "privileges" on the drive so it auto-mounts?

Thanks

---

### Post by ripcord on 2010-05-15
Have you checked permissions on the mount point directory in /media?

Otherwise, try to remount it with a new label:

system/administration/disk utility (or palimpsest from a terminal)

Unmount the drive if it's mounted. Create a new label (Edit File System Label) and then remount. This will create a new mount point folder in /media

---

### Post by demosthenese on 2010-05-15
This sounds like it is caused by the switch from hal to device-kit and policy-kit to handle drives. I've not found a solution though. USB external drives auto-mount in /media, but esata drives I have to mount by hand.

Hopefully someone will find a solution.  ](*,)

---

### Post by GuiGuy on 2010-05-15
> **ripcord said:**
> Have you checked permissions on the mount point directory in /media?

Yes. I've opened it right up. 

> 
Otherwise, try to remount it with a new label:

system/administration/disk utility (or palimpsest from a terminal)


I had already tried that, including changing the ownership of /media to my user account. No good.

> 
Unmount the drive if it's mounted. Create a new label (Edit File System Label) and then remount. This will create a new mount point folder in /media

Seems to me it will only mount in /media when  the user is sudo. Is there a way around that?

---

### Post by GuiGuy on 2010-05-15
> **demosthenese said:**
> This sounds like it is caused by the switch from hal to device-kit and policy-kit to handle drives. I've not found a solution though. USB external drives auto-mount in /media, but esata drives I have to mount by hand.


You seem to be right on this. I just plugged in a USB device and it mounted OK. The esata docking station won't :(

Oh well, it wouldn't be ubuntu if an upgrade didn't break a few things that were working splendidly in the previous version

---

### Post by demosthenese on 2010-05-15
I don't think you can entirely blame ubuntu on this. I ran into this on Debian/Sid a while back when it made the same switch. It seems that the developers of policy-kit regard all sata drives as internal and all usb drives as external. I would think that if it is there at boot time it is internal and if it appears later then it is external and so mountable by anyone in the plugdev group. But hey I'm just a user so what do I know.

---

### Post by GuiGuy on 2010-05-15
> **demosthenese said:**
> I don't think you can entirely blame ubuntu on this. 

I was being sort of tongue in cheek. Nevertheless, it is frustrating.

---

### Post by ripcord on 2010-05-15
Assuming there is no entry in /etc/fstab already, as a semi-manual workaround, you could put an entry, or entries, in  /etc/fstab (read during boot)

First unmount the device. Then define your mount point with ownership:

```
sudo mkdir /media/drive_x && sudo mount /dev/sdbX /media/drive_x  && sudo  chown GuiGuy:GuiGuy /media/drive_x
```(where GuiGuy  is your username, /media/drive_x is the mount folder and /dev/sdbX is  the device you will mount)

Use the UUID= syntax in fstab. Get the UUID using:

```
sudo blkid
```Make a note of the UUID for the applicable  device.

And to mount:

edit /etc/fstab

```
sudo gedit /etc/fstab
```and add the following line:

```
UUID=xxxxxxxxx /media/drive_x auto rw,auto,user,sync 0  0
```Where xxxxxxxxx is the UUID you discovered earlier, and  /media/drive_x is the folder you mounted earlier.

The first "auto" determines the filesystem type. Here you could have,  for example,  vfat (FAT32), ntfs, swap, ext2, ext3, etc. Auto means  auto-detect. (:

rw = read/write
auto=automount
user=any user can mount (nouser=root only)
sync=i/o is synchronous, ie immediate data write. async option defers  data transfer which is ok for fixed drives.

The last two 0 0 are dump and fsck options.

If the device is not available at boot, I think fstab should ignore the  missing device gracefully. Using the UUID rather than the /dev/sdbX  syntax should allow you to have one or more devices, as you said there  was more than one and they were removable.

If there is already an entry in fstab, check that the user option is "user" and not "nouser"

I'm not sure this will be the right solution for you, but it's worth a  try!

Hope this helps

---

### Post by GuiGuy on 2010-05-16
> **ripcord said:**
> Assuming there is no entry in /etc/fstab already, as a semi-manual workaround, you could put an entry, or entries, in  /etc/fstab (read during boot)

Thanks for that. I had already considered it but dismissed it because I have a number of HDDs that I swap in the docking station. A manual mount from  Gnome Disk Utility seems to be the easiest way for now. 

Cheers

---

### Post by Orson Wellies on 2010-05-26
I too have been driven crazy by this since I changed from Karmic to Lucid, I have many esata drives and I'm tired of mounting them by hand.
I found a helpful site that explains how to have them auto mount by hal, I used this method and they automount just fine [http://vstone.eu/2009/04/hal-and-auto-mounting-external-e-sata-devices/](http://vstone.eu/2009/04/hal-and-auto-mounting-external-e-sata-devices/)

It's quite easy to do, I'll explain how I did it in the hope it will help someone.

You need to find your drive's hal storage.serial, to do this you need to use lshal just like you would use lsusb or lspci, from a terminal.
This will spew out a lot of information to your terminal so it's better to use grep

```
orson@HP-Laptop:/$ lshal | grep 'storage.serial ='
  storage.serial = 'ST9#####410AS_5V###E3'  (string)
orson@HP-Laptop:/$ 
```This is what the above command displays without any esata drives connected, the above storage.serial string is my hard drive, it's better to do this before you connect your esata drive so as you can see any disks listed before you attatch your esata drive, so you will know which one is your esata drive.

This is the command repeated after I have attached an esata drive (doesn't need to be mounted)

```
orson@HP-Laptop:/$ lshal | grep 'storage.serial ='
  storage.serial = 'ST9#####410AS_5V###E3'  (string)
  storage.serial = 'FUJITSU_MHV2##0#H_PL_NW##ZT72##SYJ'  (string)
orson@HP-Laptop:/$ 
```As you can see I attached a Fujitsu esata drive, this is the string you will need to make your drive automount, you can repeat this command for all your esata drives to get their hal string.  Note if your drive is usb and esata you must attach with esata or you will receive a different string when attached by usb which won't automount when you attach by esata.

Once you have your string you need to edit /etc/hal/fdi/policy/preferences.fdi as root

```
orson@HP-Laptop:/$ sudo nano /etc/hal/fdi/policy/preferences.fdi

```In the preferences.fdi file you need to create a new device section for each esata drive you want mounted, as follows

```
<device>
<!-- Disk Fujitusu 80GB -->
        <match key="storage.serial" string="FUJITSU_MHV2##0#H_PL_NW##ZT72##SYJ">
        <merge key="storage.is_external" type="bool">true</merge>
    </match>
      <match key="storage.is_external" bool="true">
        <merge key="storage.removable" type="bool">true</merge>
        <merge key="storage.hotpluggable" type="bool">true</merge>
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
    <match key="@block.storage_device:storage.is_external" bool="true">
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
  </device>
```Save your file and when you plug your esata drive in it will automount to the desktop if you don't have an entry in fstab.

Just add a new section with the correct storage.serial string for every drive you want automounted.
Here is an example with 2 drives automounting

```
<device>
<!-- Disk Fujitusu 80GB -->
        <match key="storage.serial" string="FUJITSU_MHV2##0#H_PL_NW##ZT72##SYJ">
        <merge key="storage.is_external" type="bool">true</merge>
    </match>
    <match key="storage.is_external" bool="true">
        <merge key="storage.removable" type="bool">true</merge>
        <merge key="storage.hotpluggable" type="bool">true</merge>
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
    <match key="@block.storage_device:storage.is_external" bool="true">
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
  </device>

<device>
     <!-- Disk Western Digital 1TB -->
    <match key="storage.serial" string="WDC_WD10EAVS-0##7B0_WD-WC##4319##30">
        <merge key="storage.is_external" type="bool">true</merge>
    </match>
        <match key="storage.is_external" bool="true">
        <merge key="storage.removable" type="bool">true</merge>
        <merge key="storage.hotpluggable" type="bool">true</merge>
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
    <match key="@block.storage_device:storage.is_external" bool="true">
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
  </device>
```You can add as many sections as you need.
Until policy kit is fixed, and I don't think it will be soon, this is a perfect workaround for me, my drives automount just like I had them in Karmic.

Note I take no credit for this post, it's just info I found in the link at the beginning of my post and from lots of searching and reading.

Hope it helps someone.

---

### Post by GuiGuy on 2010-05-27
> **Orson Wellies said:**
> I too have been driven crazy by this since I changed from Karmic to Lucid, I have many esata drives and I'm tired of mounting them by hand.

<snip>

Note I take no credit for this post, it's just info I found in the link at the beginning of my post and from lots of searching and reading.

Hope it helps someone.

Sincere thanks for that. 

Nevertheless, it occurs to me as I reflected on the length of the detail, this is everything that is wrong with linux and why it remains a diversion for the fringe dwellers. 

Cheers

---

### Post by Orson Wellies on 2010-05-28
> **GuiGuy said:**
> Sincere thanks for that. 

Nevertheless, it occurs to me as I reflected on the length of the detail, this is everything that is wrong with linux and why it remains a diversion for the fringe dwellers. 

Cheers

You're welcome, and I completely agree.
If new users are to be converted to ubuntu, then the devs should just concentrate on ONE truly plug and play and STABLE version, instead of releasing new versions with a new theme and changing the order of window buttons, and, introducing new bugs i.e. Plymouth, fsck, external drives not automounting, the list goes on.
Curious windows users would flee after their first experience of linux.

---

