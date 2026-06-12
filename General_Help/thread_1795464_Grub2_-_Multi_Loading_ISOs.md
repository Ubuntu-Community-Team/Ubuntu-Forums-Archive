---
title: "Grub2 - Multi Loading ISOs"
date: 2011-07-02
forum: General Help
---

### Post by Roasted on 2011-07-02
I used this guide:

[http://www.youtube.com/watch?v=xf2CYSUXVh8](http://www.youtube.com/watch?v=xf2CYSUXVh8)

Annnd it didn't work. I just got a grub rescue menu. 

My grub.cfg is identical to the user's in the video, with my own edits of course to match the name of my ISO file and the name of my flash drive:

menuentry "Ubuntu" {
	set isofile="/boot/isos/ubuntu.iso"

	loopback loop $isofile
	linux {loop}/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet
splash noprompt --
	initrd (loop)/casper/initrd.lz
}

What am I doing wrong? I want to get a large 16gb flash drive and put all sorts of ISOs in there to help with troubleshooting at work. How can I accomplish this? I wanted to start small with 1 ISO and make sure it works, then add more. But as I said, it's not working. Where did I go wrong?

---

### Post by oldfred on 2011-07-02
I built mine manually, mostly from these links.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

But if you want to set it up automatically (you can still manually edit later if you want).

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I have a 4GB with several Ubuntu & repairCD on it. But with 16GB you can do a full install and include many ISO if you want. I installed to 8GB and it used about half and then I have another 8GB of data where I have a few ISOs also.

If it is a hard drive you have to add the drive, partition info or a set root.  And it may depend on your BIOS on how it sees your flash. My flash works without any reference to drive, partition, but hard drive has to have it. BIOS set Boot drive is always hd0 in grub2.

---

### Post by Roasted on 2011-07-03
> **oldfred said:**
> I built mine manually, mostly from these links.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, **create a folder for the isos and edit a grub.cfg to loop mount the isos.**
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")


This is actually what I did. I wasn't sure why I wasn't able to load even one ISO. I installed grub2 to the flash drive, created an isos folder, dropped Ubuntu 11.04 32 bit in it and named it ubuntu.iso, then tagged that iso to boot. It just came up with grub rescue.

I mean, that *is* what you're supposed to do, right?? :confused:

---

### Post by drs305 on 2011-07-03
Are you getting the 'grub rescue' prompt before you see anything else?

A grub rescue prompt means that the system isn't finding any grub files when the MBR tries to transfer control to the files in the grub folder. If you are getting a rescue prompt, it's not the menuentry that is the problem.

Or are you getting the rescue prompt once you have selected the ISO from the Grub menu? If that is the case, try manually mounting the ISO by going to the grub prompt and typing in "loopback loop (hdX,Y)/<path>/<filename>" and then using "ls (loop)/..." to see if the files exist:  (loop)/casper/vmlinuz, (loop)/casper/initrd.lz, etc.

---

### Post by Roasted on 2011-07-03
Well, I got it to work. Sort of. I seem to be having some issues working with other ISOs, such as GParted, even though I found the supposed Grub2 boot entry for it when I was googling around.

Here's an idea. Tell me if this is possible.

Is it possible... to partition my 4gb flash drive into 1gb chunks, 4 partitions. Install grub2 to it. Use Unetbootin to extract 4 different ISOs to each partition, and then manually edit the grub.cfg file to boot accordingly?

That way I could use Unetbootin, which seems to work with FAR more distro ISOs right now since it breaks the ISO open into the partition. Then I could edit grub to multi-load the partitions to boot.

Is this possible, or am I just completely off?

---

### Post by oldfred on 2011-07-03
Most of the USB creators reformat the entire flash drive.

I had some issues with gparted also. My old version worked and with 8.05 I have had to make changes. I have one stanza that works and one that does not and I do not know difference.:)

The first one was a stanza that worked with everything before v8.05. I now have tried commenting out changes. I have to have nomodeset for Ubuntu and use it everywhere now.

```
menuentry "Gparted live" {
#  insmod loopback
#  insmod iso9660
#  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile nomodeset
  initrd (loop)/live/initrd.img
}

# boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash
menuentry "Gparted Live ISO" {
set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs nomodeset
initrd (loop)/live/initrd.img

```

---

### Post by Roasted on 2011-07-04
Have you gotten Ultimate Boot CD or Clonezilla Live to work? Those are the main ones. GParted I can always use in Ubuntu's LiveCD if I need...

FYI Unetbootin works off partition only from what I can tell as long as you pre-formatted it to the structure you like. I have 4 partitions on my 1gb flash drive, each fat32. Then I have Ubuntu, Clonezilla, GParted, and UBCD on it. Think I can grub2 something up to multi load them? That way I could multi load ISOs that don't support grub2 yet...

---

### Post by oldfred on 2011-07-04
I do not boot either of those.

But I have been know to cheat and download MultbootUSB and look into the scripts that Ramesh & Sundar have created. The use some variables from the top of the script to populate the grub boot stanza, but if you understand how the stanza is built you can follow enough of  script by searching just for what you want to install.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by drs305 on 2011-07-04
I have Clonezilla working with the following entries. The ISOs are stored in sdb5's /iso folder. Note these are off a standard drive, not a Flash or USB drive.

> menuentry 'ISO Clonezilla 32                     ' 		{
set isofile="/iso/clonezilla-live-1.2.6-59-i486.iso"
loopback loop (hd1,6)$isofile
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

menuentry 'ISO Clonezilla Beta 64                ' 		{
set isofile="/iso/clonezilla-live-1.2.8-8-amd64.iso"
loopback loop (hd1,5)$isofile
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}


---

