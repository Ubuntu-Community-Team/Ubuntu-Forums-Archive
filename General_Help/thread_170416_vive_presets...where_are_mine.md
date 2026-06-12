---
title: "vive presets...where are mine?"
date: 2006-05-04
forum: General Help
---

### Post by jms830 on 2006-05-04
I installed a Vive deb for my ipod to encode video, but it did not come with any presets for video or audio settings. Can anyone post their settings that they use to convert videos to ipod or tell me where to find some presets? Thanks.

I got my vive .deb from [http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)

---

### Post by drobvice on 2006-06-02
If you have a prefences file in your .vive folder, copy this into it:

```
cpdvd_device: /dev/dvd
cpdvd_mount: /cdrom
keep_vob_checked: yes
default_preset: iPod/PSP Video
 
preset: Custom
format: avi
vcodec: mpeg4
maxrate: 1000
bitrate: 700
bufsize: 4096
aspect: 
height: 
width: 
acodec: aac
ab: 
ar: 
title: 
author: 
copyright: 
comment: Encoded by Vive

preset: iPod/PSP Video
format: mp4
vcodec: mpeg4
maxrate: 1000
bitrate: 700
bufsize: 4096
aspect: 4-3
height: 240
width: 320
acodec: aac
ab: 192
ar: 44100
title: 
author: 
copyright: 
comment: Encoded by Vive

preset: iPod/PSP Widescreen
format: mp4
vcodec: mpeg4
maxrate: 1000
bitrate: 700
bufsize: 4096
aspect: 16-9
height: 180
width: 320
acodec: aac
ab: 192
ar: 44100
title: 
author: 
copyright: 
comment: Encoded by Vive 

preset: Default AVI
format: avi
vcodec: mpeg4
maxrate: 1000
bitrate: 700
bufsize: 4096
aspect: 
height: 
width: 
acodec: mp3
ab: 192
ar: 44100
title: 
author: 
copyright: 
comment: Encoded by Vive

preset: Default MPEG
format: mp4
vcodec: mpeg4
maxrate: 1000
bitrate: 200
bufsize: 4096
aspect: 
height: 
width: 
acodec: mp3
ab: 192
ar: 44100
title: 
author: 
copyright: 
comment: Encoded by Vive


preset: Default OGM
format: avi
vcodec: xvid
maxrate: 1000
bitrate: 700
bufsize: 4096
aspect: 
height: 
width: 
acodec: vorbis
ab: 192
ar: 44100
title: 
author: 
copyright: 
comment: Encoded by Vive



```

I added a 16:9 profile for iPod as well.  I have yet to test the video on the iPod, but I just changed the aspect ratio from the default iPod/PSP profile.  Hope this helps (if you are still looking for it).  I found this thread becuase I was looking for these presets as well.  I decided to install from tar.gz file and they were included.

---

