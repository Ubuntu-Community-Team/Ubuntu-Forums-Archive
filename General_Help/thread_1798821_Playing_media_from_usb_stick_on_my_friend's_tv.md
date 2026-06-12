---
title: "Playing media from usb stick on my friend's tv"
date: 2011-07-06
forum: General Help
---

### Post by t0p on 2011-07-06
My friend recently got a new tv.  It's got a usb input, and according to the instructions it can play video and image files from the stick.

I've got some home-shot video files of my friend's recently-deceased dog.  They're .avi files.  I tried to play them, but the tv refused to play because of the file format of the stick: the instructions say the v only supports older Windows formats - ie fat not ntfs.  So, I reformatted the stick to fat16, recopied the video files and tried again.  Now the sees the files but says it can't play the files because they're in an unsupported format.  I've tried fat32 too.

The instructions specifically say that .avi is a supported file format.  S why oh why won't the vids play?  My friend really misses the dog and would love to be able to watch them.  I can play them on my computers, so I can take my netbook to his house or he can come visit my home and watch them on my desktop.  But that's highly inconvenient.

Any ideas people?  Cheers.

---

### Post by CatKiller on 2011-07-06
> **t0p said:**
> The instructions specifically say that .avi is a supported file format. 

AVI is a container format. It could be any encoding inside.

If you can't find out what encoding the TV supports, it might be worth picking one that's used by other things, like MPEG-2 (used by DVDs) or H.264/MPEG4 AVC or VC-1 (both used by Blu-Rays).

I can't give you specific advice because video encoding makes me cry. It might give you a starting point, though.

---

### Post by decoherence on 2011-07-06
Like CatKiller said, knowing that it's an AVI is pretty useless (and the TV claiming that they 'support' AVI is only slightly less than useless.) 

You can run the following on the video to get a bit more information

```
ffmpeg -i *yourvideo.avi*
```

The following command will transcode it in to MJPEG format -- if the TV doesn't support that, it is lame.

```
ffmpeg -i <input_file> -vcodec mjpeg -qscale 1 -an output.avi 
```

---

