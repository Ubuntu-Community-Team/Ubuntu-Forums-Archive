---
title: "Error mounting an iso file"
date: 2011-11-29
forum: General Help
---

### Post by Hjensen on 2011-11-29
I've done this many times before, but I can't for the life of me figure out what I'm doing wrong this time. I'm trying to mount an .iso of my matlab using some variant of

```
mount -o loop -t iso9660 matlab.iso ~/Desktop/ml
```It gives me the error:
```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```The presumably relevant part of dmesg | tail is
```

[  828.192895] ISOFS: Unable to identify CD-ROM format.
[ 1549.845979] ISOFS: Unable to identify CD-ROM format.

```I have also tried without the "iso9660", but then it just tells me to specify the file system type. Furthermore, I've tried to mount it using both AcetoneISO and Gmount-iso. No luck there either. Any suggestions?

---

### Post by mcduck on 2011-11-29
Have you tried the simple option, right-click the .iso file and select "Mount using Archive Mounter" (or something like that, I can't rember the exact name of the option right now...)

That should do exactly what you are trying to do. Assuming you are runing a fairly recent Ubuntu version, and using Gnome desktop, of course...

Also are you sure it's a CD image? Perhaps it's a DVD image and uses UDF as the file system instead?

---

### Post by Hjensen on 2011-11-29
> **mcduck said:**
> Have you tried the simple option, right-click the .iso file and select "Mount using Archive Mounter" (or something like that, I can't rember the exact name of the option right now...)

That should do exactly what you are trying to do. Assuming you are runing a fairly recent Ubuntu version, and using Gnome desktop, of course...

Also are you sure it's a CD image? Perhaps it's a DVD image and uses UDF as the file system instead?

Yeah, I've tried using the archive manager. I don't think it's a DVD image, but what would I have to change in order to mount it? I thought it worked the same way.

---

### Post by mcduck on 2011-11-29
> **Hjensen said:**
> Yeah, I've tried using the archive manager. I don't think it's a DVD image, but what would I have to change in order to mount it? I thought it worked the same way.

It should mount the same way, but you need to use a different option for the filesystem, DVDs (and also some CDs) use UDF file system, not iso9660.

Of course if the archive mounter fails, like all the other tools you've tried, there's always the possibility that the .iso file you are trying to mount is corrupted. In that case try downlaoding the image again, and if possible use a torrent download (torrent protocol will automatically check the files for errors, making sure you get a working image)

---

### Post by Hjensen on 2011-11-29
I have now tried using a script which takes into account that it might be a UDF file system, but it just gives me an error. I've obtained the iso file from a friend who has it working on his computer (with the same ubuntu distribution as mine). However, to get the file onto my computer, we had to split it up and put it back together (using cat xa* > matlab.iso). Do you reckon this could've messed up the file in some way? I've never heard about such a thing happening before, but it might be a possibility.

---

### Post by mcduck on 2011-11-29
> **Hjensen said:**
> I have now tried using a script which takes into account that it might be a UDF file system, but it just gives me an error. I've obtained the iso file from a friend who has it working on his computer (with the same ubuntu distribution as mine). However, to get the file onto my computer, we had to split it up and put it back together (using cat xa* > matlab.iso). Do you reckon this could've messed up the file in some way? I've never heard about such a thing happening before, but it might be a possibility.

Sure, it's possible. And files *can* end corrupted when transferred even if they are not splitted. It's definitely not a common issue (unless there's some kind of hardware problem), but still possible and happens sometimes.

If you can get your frend to generate an MD5 checksum for the file, you could do the same to check if it's OK or not. (simple "*[I]md5sum filename*[/I]" should do the trick on any Ubuntu system)

---

