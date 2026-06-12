---
title: "Audio Previews in Konqueror"
date: 2006-02-21
forum: General Help
---

### Post by AdrianVeidt on 2006-02-21
When I hover the mouse over an audio file, the file should start playing. I activated audio previews in the 'View' menu, and it doesn't work for mp3s. I have an ogg here, which does work. I started Konq from the terminal to capture errata. When I hover over the ogg, which plays, there is no output. However, when I hover over an mp3, the following output happens:
```

kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-mpeg not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-mpeg not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-mpeg2 not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-mpeg2 not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-msmpeg not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-msmpeg not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/vnd.mpegurl not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/vnd.mpegurl not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-mpegurl not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-mpegurl not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-ms-wax not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-ms-wax not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-ms-wmp not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-ms-wmp not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-afs not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-afs not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wmp not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wmp not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wma not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wma not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wvx not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wvx not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wmx not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-ms-wmx not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-ms-asf not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-ms-asf not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-pls not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-pls not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/vnd.mpegurl not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/vnd.mpegurl not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-realaudio not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype audio/x-realaudio not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-pn-realaudio not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-pn-realaudio not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-realvideo not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-realvideo not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-pn-realvideo not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-pn-realvideo not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-pn-realvideo-plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-pn-realvideo-plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/vnd.rn-realplayer not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/vnd.rn-realplayer not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/nsv not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/nsv not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-divx not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype video/x-divx not found
```

This is where it stops. The mime-type Mpeg Layer-3 Audio is in Konq's database, which is viewable from 'Configure Konqueror->File Associations->Audio->x-mp3', which has exactly the same features as the ogg entry "x-vorbis", or "vorbis". Moreover the only audio type which appears to work for me is ogg. I have several other types here, and none of them preview.

---

### Post by digitalkarabao on 2006-05-15
i second the motion. same issue happens on my machine. cannot preview (on mouse hover) audio files aside from .ogg.

---

### Post by Shay Stephens on 2006-05-21
I have the oposite problem, I can preview mp3 but not ogg.  Anyone know why or how to fix?

---

### Post by Shay Stephens on 2006-05-23
[QUOTE=Shay Stephens]I have the oposite problem, I can preview mp3 but not ogg.  Anyone know why or how to fix?[/QUOTE]

Just found out in this post how to fix it:
[http://ubuntuforums.org/showpost.php?p=1044324&postcount=9](http://ubuntuforums.org/showpost.php?p=1044324&postcount=9)

So I used synaptic to load vobis-tools and ogg is now previewing.

---

