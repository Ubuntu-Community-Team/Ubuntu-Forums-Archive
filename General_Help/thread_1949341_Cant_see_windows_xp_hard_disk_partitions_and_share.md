---
title: "Cant see windows xp hard disk partitions and shared fold"
date: 2012-03-30
forum: General Help
---

### Post by pellyhawk on 2012-03-30
I am new to Linux and recently installed ubuntu 10.04 based on a vmware virtual machine at windows xp. when open ubuntu, left-clicking places->desktop, I can see windows xp hard disk partitions and folds and files in them, but today I cannot.

Besides, I installed a shared fold based on the vmware tool. I can see some shared files. Today when logging into windows xp, I copied some files and folds into the shared files, but these new-copied files and folds cannot be seen in the shared fold when I logged into the virtual ubuntu.

Any help will be appreciated. Thanks in advance.

---

### Post by imachavel on 2012-03-30
that's weird, if you created a shared folder, then you should be able to see it. I don't know are you putting your files in the shared folder? How do you access the files anyway? I don't know why it would work before and not know if you configured it correctly.

A common trouble shooting issue to fixing virtual machine issues, go to the site of the provider who you downloaded the virtual machine from, look for guest additions or extensions to install. Good luck man

---

### Post by pellyhawk on 2012-03-30
After reboot WinXP, now I can see shared fold.

However, WinXP hard disk partitions still cannot be seen. Yesterday, they can be seen and seem OK.

> **imachavel said:**
> that's weird, if you created a shared folder, then you should be able to see it. I don't know are you putting your files in the shared folder? How do you access the files anyway? I don't know why it would work before and not know if you configured it correctly.

A common trouble shooting issue to fixing virtual machine issues, go to the site of the provider who you downloaded the virtual machine from, look for guest additions or extensions to install. Good luck man

---

### Post by pellyhawk on 2012-03-30
Perhaps I need to describe the issue in detail.

Before this issue happened today, while left-clicking Places->Desktop, a fold will emerge(without installing Samba). At the left part of the fold, many things can be seen, such as "Desktop", "File System", "Network" "Floppy Drive" and winxp hard disk partitions. Left-click any of them(on top of them, there is a "Places"), you will see files and sub-folds at the right part of the fold. Especially, left-click one of the winxp hard disk partitions, files and sub-folds built in winxp will be seen.

But now, winxp hard disk partitons cannot be seen at the left part of the fold, thus those files and sub-folds built in winxp cannot be seen as well. What's wrong with it?

Thanks a lot.

---

### Post by varunendra on 2012-03-30
> **pellyhawk said:**
> Perhaps I need to describe the issue in detail.

Before this issue happened today, while left-clicking Places->Desktop, a fold will emerge(without installing Samba). At the left part of the fold, many things can be seen, such as "Desktop", "File System", "Network" "Floppy Drive" [COLOR=Red]**and winxp hard disk partitions**[/COLOR]. Left-click any of them(on top of them, there is a "Places"), you will see files and sub-folds at the right part of the fold. Especially, left-click one of the winxp hard disk partitions, files and sub-folds built in winxp will be seen.

But now, winxp hard disk partitons cannot be seen at the left part of the fold, thus those files and sub-folds built in winxp cannot be seen as well. What's wrong with it?

Thanks a lot.
Maybe a full screenshot of the VMware window (with its borders) while it is running could help. AFAIK, you can't see any file/folder/partition of the host system from within a virtual machine (it only 'sees' the virtualized hardware) as a local part of it, unless you explicitly add a 'physical' HDD/partition to it (which can be extremely dangerous if the host OS is also accessing it at the same time!).

I believe you might have added a 'physical' partition/drive during the creation of the virtual machine, and now it is somehow disconnected. The screenshot may reveal if a device is available but disconnected.

Posting the contents of ".vmx" file (located in the folder where the VM resides) may also reveal if a physical drive/partition is attached to the VM. That file can be opened on notepad (pay attention to lines that start with "IDE" or "SCSI" in it).

But for very specific issues, I think you may get the best kind of support on VMware's forum itself.

---

### Post by pellyhawk on 2012-03-30
Thanks you.

I upload 2 screenshots to describe this issue more clearly.
The former.png describes the status before and you can see "54 GB Filesystem&#65292;65 GB Filesystem&#65292;65 GB Filesystem&#65292;65 GB Filesystem", and the current.png describes the current status, "54 GB Filesystem&#65292;65 GB Filesystem&#65292;65 GB Filesystem&#65292;65 GB Filesystem" cannot be seen.

The VM Player is located at "D:\VMware", while Ubuntu located at"D:\My Virtual Machines".I post Ubuntu.vmx(its path is "D:\My Virtual Machines\Ubuntu") here:

```
.encoding = "GBK"
config.version = "8"
virtualHW.version = "7"
numvcpus = "2"
scsi0.present = "TRUE"
scsi0.virtualDev = "lsilogic"
memsize = "1024"
scsi0:0.present = "TRUE"
scsi0:0.fileName = "Ubuntu.vmdk"
ide1:0.present = "TRUE"
ide1:0.autodetect = "TRUE"
ide1:0.deviceType = "cdrom-image"
floppy0.startConnected = "FALSE"
floppy0.fileName = ""
floppy0.autodetect = "TRUE"
ethernet0.present = "TRUE"
ethernet0.connectionType = "bridged"
ethernet0.wakeOnPcktRcv = "FALSE"
ethernet0.addressType = "generated"
usb.present = "TRUE"
ehci.present = "TRUE"
sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"
serial0.present = "TRUE"
serial0.fileType = "thinprint"
pciBridge0.present = "TRUE"
pciBridge4.present = "TRUE"
pciBridge4.virtualDev = "pcieRootPort"
pciBridge4.functions = "8"
pciBridge5.present = "TRUE"
pciBridge5.virtualDev = "pcieRootPort"
pciBridge5.functions = "8"
pciBridge6.present = "TRUE"
pciBridge6.virtualDev = "pcieRootPort"
pciBridge6.functions = "8"
pciBridge7.present = "TRUE"
pciBridge7.virtualDev = "pcieRootPort"
pciBridge7.functions = "8"
vmci0.present = "TRUE"
roamingVM.exitBehavior = "go"
displayName = "Ubuntu"
guestOS = "ubuntu"
nvram = "Ubuntu.nvram"
virtualHW.productCompatibility = "hosted"
printers.enabled = "TRUE"
gui.exitOnCLIHLT = "FALSE"
extendedConfigFile = "Ubuntu.vmxf"
checkpoint.vmState = ""
ide1:0.startConnected = "FALSE"
ethernet0.generatedAddress = "00:0c:29:d8:24:a9"
tools.syncTime = "FALSE"
uuid.location = "56 4d d2 09 42 a7 e1 71-e6 3c c4 59 8b d8 24 a9"
uuid.bios = "56 4d d2 09 42 a7 e1 71-e6 3c c4 59 8b d8 24 a9"
cleanShutdown = "FALSE"
replay.supported = "FALSE"
unity.wasCapable = "TRUE"
replay.filename = ""
scsi0:0.redo = ""
pciBridge0.pciSlotNumber = "17"
pciBridge4.pciSlotNumber = "21"
pciBridge5.pciSlotNumber = "22"
pciBridge6.pciSlotNumber = "23"
pciBridge7.pciSlotNumber = "24"
scsi0.pciSlotNumber = "16"
usb.pciSlotNumber = "32"
ethernet0.pciSlotNumber = "33"
sound.pciSlotNumber = "34"
ehci.pciSlotNumber = "35"
vmci0.pciSlotNumber = "36"
vmotion.checkpointFBSize = "16777216"
ethernet0.generatedAddressOffset = "0"
vmci0.id = "-1948769111"
ide1:0.fileName = "D:\VMware\VMware Player\linux.iso"
serial1.present = "TRUE"
serial1.autodetect = "TRUE"
isolation.tools.hgfs.disable = "FALSE"
sharedFolder.maxNum = "1"
serial1.startConnected = "FALSE"
sharedFolder0.present = "TRUE"
sharedFolder0.enabled = "TRUE"
sharedFolder0.readAccess = "TRUE"
sharedFolder0.writeAccess = "TRUE"
sharedFolder0.hostPath = "D:\VBox_Shared"
sharedFolder0.guestName = "VBox_Shared"
sharedFolder0.expiration = "never"
tools.remindInstall = "FALSE"
usb:1.present = "TRUE"
usb:1.deviceType = "hub"
debugStub.linuxOffsets = "0x0,0xffffffff,0x0,0x0,0x0,0x0,0x0,0x0,0x0,0x0,0x0,0x0,0x0,0x0"
usb.autoConnect.device0 = ""

```

---

