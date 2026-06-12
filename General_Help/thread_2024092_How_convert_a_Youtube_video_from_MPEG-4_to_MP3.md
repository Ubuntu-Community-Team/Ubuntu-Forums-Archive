---
title: "How convert a Youtube video from MPEG-4 to MP3?"
date: 2012-07-13
forum: General Help
---

### Post by BSG Fan on 2012-07-13
using **Video DownloadHelper 4.9.9**

yes, a simple music video from MPEG-4 to MP3?

MPEG-4 is too heavy in megabytes but MP3 is too ligh if you save them in a CD-ROM with other MP3 files of music.

I tried, but it does not work:
Converter Options,
the java script window says that External Application is missed,
and a window of Preferences shows,
but I have no idea how to fix the Conversion
.... but again the same windows show up.
What I do?

my question is divided into 2 questions:

1- from MPEG-4 to MP3 (online) 

2- from MPEG-4 to MP3 (the video already in the computer)

Thank in advance!

:o

---

### Post by Kopkins on 2012-07-13
For already on the computer, you should be able to use VLC media player's convert feature to convert your mpeg-4 to mp3. 

From VLC > Media > Convert / Save.

You should be able to look up simple tutorials on how to use this feature. 

Best of luck,
Kopkins

---

### Post by Zvlwab on 2012-07-13
run the following command
```
ffmpeg i- /path/to/mp4/file.mp4 -aq 2 -map_meta_data 0:0,s0 /path/to/new/mp3/file.mp3
```
This converts the file to an mp3 V2 file and keeps the metadata.

OR

use to get a constant bitrate
```
ffmpeg i- /path/to/mp4/file.mp4 -b 320000 -map_meta_data 0:0,s0 /path/to/new/mp3/file.mp3
```
This converts the file to an mp4 320kbps file and keeps the metadata.

Do note that you can't make the audio quality any better by entering numbers higher than those of the original file.

---

### Post by nothingspecial on 2012-07-13
Downloading videos from youtube then extracting the audio is against their ToS.

Closed.

---

