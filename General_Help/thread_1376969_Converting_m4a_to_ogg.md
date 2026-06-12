---
title: "Converting m4a to ogg"
date: 2010-01-09
forum: General Help
---

### Post by Arenlor on 2010-01-09
I'd prefer a command line version if possible. Batch use would be best.

---

### Post by nothingspecial on 2010-01-09
Converting one lossy audio format to another will just result in a lossier file.

If you must, check out ffmpeg

To enable the best performance see [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by ron999 on 2010-01-09
Hi

ffmpeg will do the job.

When I look in the 'presets' folder of WinFF he uses these settings:-
```
ffmpeg -i input.m4a -acodec vorbis -aq 60 -vn -ac 2 output.ogg

```
But if you use this from the command line, or using the WinnFF gui, you'll lose any tags.

Personally I would just use SoundConverter for a job like this. It would try and retain the tags.
But if you want to use cli for your own reasons then that's fine. Develop a script to batch convert.
:)

---

### Post by nothingspecial on 2010-01-09
> **ron999 said:**
> Hi

ffmpeg will do the job.

When I look in the 'presets' folder of WinFF he uses these settings:-
```
ffmpeg -i input.m4a -acodec vorbis -aq 60 -vn -ac 2 output.ogg

```
But if you use this from the command line, or using the WinnFF gui, you'll lose any tags.

Personally I would just use SoundConverter for a job like this. It would try and retain the tags.
But if you want to use cli for your own reasons then that's fine. Develop a script to batch convert.
:)

m4a will not work nice until you do what is outlined in the link I posted,

---

### Post by Arenlor on 2010-01-09
This is the script I made. Seems to work well enough. Note that because it uses rename it is Debian derivative specific.
```
#!/bin/bash
# m4a2ogg converts all m4a to ogg in a directory.
# Arenlor
for i in *.m4a
do
        ffmpeg -y -i "$i" "$i".wav
        oggenc -q10 "$i".wav
done
rename 's/m4a.ogg/ogg/g' *
rm *.wav
rm *.m4a
exit 0
```

---

### Post by andrew.46 on 2010-01-10
Hi ron,

> **ron999 said:**
> When I look in the 'presets' folder of WinFF he uses these settings:-
```
ffmpeg -i input.m4a -acodec vorbis -aq 60 -vn -ac 2 output.ogg

```
But if you use this from the command line, or using the WinnFF gui, you'll lose any tags.

Newer versions of FFmpeg have an option to preserve the meta tags:

```

andrew@skamandros~$ ffmpeg -h | grep 'map_meta_data'
[...]
-map_meta_data outfile:infile  set meta data information of outfile from infile
```

This would make the commandline:

```

ffmpeg -i input.m4a \
	-acodec vorbis -aq 60 -vn -ac 2 \
	-map_meta_data outfile.ogg:input.m4a \
	output.ogg

```

I have to admit that I have not used this option extensively but it has worked flawlessly on the half a dozen time I have used it. Thus I am not completely sure how many media types it will work with...

All the best,

Andrew

---

### Post by ron999 on 2010-01-10
Hi Andrew
That's very interesting about ffmpeg's meta data.
My version of ffmpeg has the option too.

> ron@ubuntu:~$ ffmpeg -h | grep 'map_meta_data'
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
[...]  
-map_meta_data outfile:infile  set meta data information of outfile from infile

I tested it using this command:-

```
ffmpeg -i "03 - Flying.m4a" -acodec vorbis -aq 60 -vn -ac 2 -map_meta_data outfile.ogg:"03 - Flying.m4a" output.ogg

```
Then I analysed the output file with MediaInfo:-

> General
Complete name                    : /home/ron/Desktop/output.ogg
Format                           : OGG
File size                        : 3.06 MiB
Duration                         : 2mn 15s
Overall bit rate                 : 189 Kbps

Audio
ID                               : 0 (0x0)
Format                           : Vorbis
Duration                         : 2mn 15s
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Resolution                       : 16 bits

It doesn't seem to be working, there's no tag information there.

When I converted the file using SoundConverter the tags seem intact:-

> General
Complete name                    : /home/ron/Desktop/03 - Flying.ogg
Format                           : OGG
File size                        : 3.00 MiB
Duration                         : 2mn 15s
Overall bit rate                 : 186 Kbps
Album                            : Magical Mystery Tour
Track name                       : Flying
Performer                        : The Beatles
Genre                            : Rock/Classic Rock/Pop
Copyright                        : © 2009 EMI Records Ltd
Comment                          : Lavf52.31.0
COMPOSER                         : The Beatles

Audio
ID                               : 1317219419 (0x4E832C5B)
Format                           : Vorbis
Format settings, Floor           : 1
Duration                         : 2mn 15s
Bit rate mode                    : Constant
Bit rate                         : 192 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Resolution                       : 16 bits
Stream size                      : 3.10 MiB
Writing library                  : libVorbis 1.2 (UTC 2007-06-22)


So maybe ffmpeg's meta data option works for some types of files and not others, as you hinted.

---

