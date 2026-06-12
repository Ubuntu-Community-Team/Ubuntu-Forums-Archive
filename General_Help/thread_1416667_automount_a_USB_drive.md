---
title: "automount a USB drive"
date: 2010-02-26
forum: General Help
---

### Post by sixstringssteve on 2010-02-26
Here is another noob question form you ol' buddy Steve
 
I have a machine running karmic server and it will not let me mount a USB drive unless I go throught the terminal process of mounting the drive.  This becomes a real pain in the keister.  Can someone help me activate automount on a server edition.  My workstations do it automatically, why can't my server?

---

### Post by johngreth on 2010-02-26
This might help: [https://help.ubuntu.com/community/Mount/USB#Configuring%20Automounting](https://help.ubuntu.com/community/Mount/USB#Configuring%20Automounting)

---

### Post by sixstringssteve on 2010-03-01
I tried that one, auto-mount is set on, but when I insert the USB drive it says Unable to Mount, Not Authorized
 
I'm telling you, I love workstation Ubuntu, but Server Ubuntu is a pain.

---

### Post by johngreth on 2010-03-01
did you install usbmount as well?

---

### Post by DawieS on 2010-03-01
[COLOR=Red][/COLOR][COLOR=Black]You probably have a NTFS file-system on that USB drive. I don't have the **server** edition, but have tested just about all possible combinations of mounting options on the **desktop** edition.

You can change the default disk behavior of your Karmic server by editing the following file using the **'sudo gedit**' command in a terminal:

/usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

If you have external disks plugged in through back-plates on the motherboard, they are seen as internal by Karmic. To be able to mount without authorization, look for the following header:

  <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">

under that will be something like this:

<defaults>
    <allow_any>no</allow_any>
    <allow_inactive>no</allow_inactive>
    <allow_active>[COLOR=Red]auth_admin_keep[/COLOR]</allow_active>
</defaults>

change the highlighted one to:

    <allow_active>[COLOR=Red]yes[/COLOR]</allow_active>

Also check whether the first header is also marked as '[COLOR=Red]yes[/COLOR]' on the server edition (I cannot remember whether USB drives with NTFS was able to automount):

  <action id="org.freedesktop.devicekit.disks.filesystem-mount">

Save, exit and reboot. You should now be able to auto-mount your NTFS drives.

Notes:
 - These changes may be overwritten by an upgrade and may require re-doing.
 - It is best not to have any external drives listed in the /etc/fstab file, especially if they contain NTFS file-systems. Listing them may result in drives appearing doubled up in the file browser, cross-mounting to wrong drives, unable to unmount without reboot, etc.[/COLOR]

---

### Post by sixstringssteve on 2010-03-04
Installed usbmount and it didn't work either.  The usb drive is FAT16 format and works fine when manually mounted.  Usbmount installed but when I insert the drive it still says unauthorized.  i understand and enjoy the added security with Ubuntu, but when it gets in your way so far is you cannot due simple tasks, why not stay with Windows for the server part?

---

### Post by bodhi.zazen on 2010-03-04
By default usbmount does not recognize FAT partitions, lol

So either use an alternate file system or edit /etc/usbmount/usbmount.conf

On the line "FILESYSTEMS" make sure you have vfat listed. You can try adding fat16.

Next, reading the config file, it suggests the mount points must exist, so ...

```
sudo mkdir /media/usb{0,1,2,3,4,5,6,7}
```

And try again.

If it fails, post

```
dmesg tail
```

See if we have any error messages.

---

### Post by sixstringssteve on 2010-03-04
You'll have to excuse me, I'm new to the Linux scene here so I am a bit slow.  The config file shows both vfat and I added fat16.  The /media/usb0 - /media/usb7 already exist in the filesystem.  I tried to run the test to show you, but it is longer than the scrolling allows in the terminal, so I can only mount the letter part of the report.  i know how to save a report to  text doc in windows but not in Ubuntu.  Can you give me a hint here?

---

### Post by bodhi.zazen on 2010-03-04
you re-direct with a >

command > output.txt

for dmesg we need only the last few lines.

plug in your usb and run

```
dmesg | tail
```

forgot the pipe in my last post

---

### Post by sixstringssteve on 2010-03-04
here is the last bit of the report.  This is after I plug in the USB drive and it gives me the Unable to Mount, Not Authorized warning.
 
 
[537770.423602] usb 1-3: USB disconnect, address 11
[537800.420045] usb 1-3: new high speed USB device using ehci_hcd and address 12
[537800.795099] usb 1-3: configuration #1 chosen from 1 choice
[537800.804266] scsi12 : SCSI emulation for USB Mass Storage devices
[537800.804646] usb-storage: device found at 12
[537800.804652] usb-storage: waiting for device to settle before scanning
[537805.802906] usb-storage: device scan complete
[537805.804009] scsi 12:0:0:0: Direct-Access HP v100w 2048 PQ: 0 ANSI: 0 CCS
[537805.804556] sd 12:0:0:0: Attached scsi generic sg2 type 0
[537805.811216] sd 12:0:0:0: [sdb] 3915776 512-byte logical blocks: (2.00 GB/1.86 GiB)
[537805.812251] sd 12:0:0:0: [sdb] Write Protect is off
[537805.812257] sd 12:0:0:0: [sdb] Mode Sense: 43 00 00 00
[537805.812260] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[537805.815486] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[537805.815494] sdb: sdb1
[537805.818624] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[537805.818633] sd 12:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by bodhi.zazen on 2010-03-04
I suspect it has to do with the FAT16 file system, although I am not sure.

would you be willing to reformat the device to ext2 ?

my only other thought , do you have a line in your fstab ?

---

### Post by vikjon0 on 2010-03-15
I am having the same problem when running gnome by startx instead of gdm. Is this what you are doing? I have no clue how to fix it yet. Except sudo startx...then it works.

---

### Post by sixstringssteve on 2010-03-15
anyone have an answer for me here?

---

