---
title: "Xoom Banshee Sync"
date: 2012-02-18
forum: General Help
---

### Post by drdanielfc on 2012-02-18
Hello all,

So I've been trying to get my wifi xoom to sync music with Banshee. Here's a summary of what I've done so far:

[SIZE="4"]Getting File Access of any Kind[/SIZE]

**1. Installed everything that has anything to do with MTP**.
Nautilus would not recognize the device and mounting it was a long, convoluted process.

**2. Editing /etc/udev/rules.d/51-android.rules**
The first method I tried was to add the following:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", MODE="0777", RUN+="/bin/bash -c 'mkdir -p /media/Xoom && mtpfs /media/Xoom -o allow_other'"
ACTION=="remove", RUN+="/bin/fusermount -u /media/Xoom/", RUN+="/bin/rmdir /media/Xoom/" 
```
Advantages
[LIST]
[*]Fast file access from nautilus
[/LIST]
Disadvantages
[LIST]
[*]Need to navigate to /media/Xoom instead of it being in nautilus (could be remedied by changing mode from 0777 to 0666)
[*]Doesn't get recognized in Banshee
[/LIST]

**3. Editing /etc/udev/rules.d/51-android.rules (attempt 2)**
Afterwards I tried the following:
```
SUBSYSTEM=="usb", SYSFS{idVendor}=="22b8", MODE="0666", OWNER="dcentore"
```
Advantages
[LIST]
[*]Recognized correctly as a device in nautilus
[*]Banshee sees it!
[/LIST]
Disadvantages
[LIST]
[*]Very slow file access from nautilus. Acceptable from banshee.
[*]Takes forever (over a minute) to initialize when I first plug it in
[/LIST]

[SIZE="4"]Getting Banshee to Sync[/SIZE]
So I am using method 3 right now because it is the only one I can even get Banshee to recognize my device with.

**Nothing**
So when I do nothing at all Banshee syncs all my files correctly. To the root folder of my device. This is a terrible mess and completely unnacceptable.

**.is_audio_player**
It is suggested [here]("http://forum.xda-developers.com/showthread.php?t=624240") that I put a file named [FONT="Courier New"].is_audio_player[/FONT] in the root of my device and put the following inside it:
```
audio_folders=Music/
folder_depth=2
output_formats=audio/mpeg,audio/mp3,audio/x-aac,audio/flac
cover_art_file_name=AlbumArt.jpg
cover_art_file_type=jpeg
cover_art_size=320
```

That causes it to sync all my music correctly *the first time.* After I unplug my xoom, and plug it back in, then all hell breaks loose (okay, not really). Basically it appears that the .is_audio_player file becomes corrupted and banshee decides to sync all those files into root but with a severely convoluted folder structure that makes it miserable to delete all the files afterwards. When I try to open the corrupted file, gedit gives the following error:
```
Could not open the file gphoto2://[usb:001,011]/.is_audio_player.
gedit cannot handle gphoto2: locations.
```
The file size, however, has the same number of bytes as it did before.


Can someone please help me with this?
Regards,
Daniel

---

### Post by drdanielfc on 2012-04-27
bump

---

### Post by techsupport on 2012-04-27
> **drdanielfc said:**
> bump

Ubuntu 12.04 LTS no longer includes Banshee by default. Way way way too many issues.

Maybe someone here knows?

---

