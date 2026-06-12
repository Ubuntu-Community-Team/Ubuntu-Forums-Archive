---
title: "Force DX9(DirectX9) In Vmware Player"
date: 2009-09-23
forum: General Help
---

### Post by dvl300 on 2009-09-23
Here's my Windows XP Proffesional
.vmx file
```
#!/usr/bin/vmware
.encoding = "UTF-8"
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "1020"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/sr1"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "FALSE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d d7 cc e8 e6 df 22-e1 86 81 ab c0 ee f3 c4"
uuid.bios = "56 4d d7 cc e8 e6 df 22-e1 86 81 ab c0 ee f3 c4"
ethernet0.generatedAddress = "00:0c:29:ee:f3:c4"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = ""
tools.remindInstall = "FALSE"

extendedConfigFile = "WindowsXPPro.vmxf"

floppy0.clientDevice = "FALSE"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

vmotion.checkpointFBSize = "134217728"
svga.vramSize = 67108864
vmmouse.present = FALSE
# Experimental!
# Accelerated 3-D Graphics
mks.enable3d = "TRUE"
```

Hmmm any suggestions?

---

### Post by dvl300 on 2009-09-24
Is there any other way I can force DX9

---

