---
title: "f-spot error when trying to import from camera"
date: 2009-08-10
forum: General Help
---

### Post by chucky chuckaluck on 2009-08-10
this is a pretty fresh installation of jaunty. i've never used f-spot before. i had assumed my camera would have been automounted as it has been in previous versions of ubuntu, but it wasn't (at least, it didn't appear to be when i opened nautilus and there was no desktop icon). when i tried f-spot, it had my camera listed as an option from which to import. i tried it and got the following in the terminal...

fuscia@fuscianator:~$ f-spot
[Info  13:31:19.002] Initializing DBus
[Info  13:31:19.175] Initializing Mono.Addins
[Info  13:31:19.472] Starting new FSpot server
[Info  13:31:20.840] Starting BeagleService
[Info  13:31:20.841] Hack for gnome-settings-daemon engaged
item ImportCommand+SourceItem
Testing gphoto path = usb:
PortInfo Universal Serial Bus, usb:
Error GeneraError: LibGPhoto2.GPhotoException: Unspecified error
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000]

i also tried adding the following to my /etc/fstab...

/dev/sdb1       /home/fuscia/camera        vfat        user,noauto,exec 0       0

which had worked just fine in previous versions of ubuntu with the same camera on the same laptop, but when i did *sudo mount camera*, i got ...

mount: special device /dev/sdb1 does not exist

ideally, i would just like to mount my camera the way i used to and access my pics from either the terminal, file manager, image viewer or gimp and skip f-spot, but i guess i would need to get that */dev/whatever* mess worked out.

---

### Post by Tamlynmac on 2009-08-10
I experienced a similar problem and switched to "GThumb Image Viewer" (menu/file/import photos) it took a moment to check for a driver and then downloaded a generic driver with which I've had no problem. My camera does not show up on the list of available camera drivers anymore, but as I said the generic driver appears to work fine for importing and deleting the pics from my camera.

I wonder if the driver simply is no longer available to F-Spot for some reason.

---

### Post by chucky chuckaluck on 2009-08-10
it seems ubuntu now reads cameras mostly as PTP rather than mass storage devices. it now autodetects but doesn't mount my camera. i'm not used to this, so i guess i'll have to mess with it a bit. thanks for the response.

update: dumping both f-spot and gthumb allows me to open up my camera wherever i want (and a lot faster, too). cool! problem solved.

---

