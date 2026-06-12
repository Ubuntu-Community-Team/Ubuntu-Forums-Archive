---
title: "ffmpeg conversion removing aac tags"
date: 2006-03-27
forum: General Help
---

### Post by the7trumpets on 2006-03-27
I finally got ffmpeg installed with faac support so that I can convert my apple lossless audio into 128 kb/s aac for lower bitrate streaming offsite. The following command line does the trick:

ffmpeg -i [input file.m4a] -acodec aac -ab 128 [output file.m4a]

However, any tags applied to my input file in apple lossless format are not applied to the output file. How can I get the tags to be applied within ffmpeg? If that's impossible, is there some other program that I can copy the tags from one file (apple lossless, inside m4a container) and write them to another file (aac, inside m4a container)? 

Also, are there any settings to increase quality? I tried '-hq' after seeing it in the documentation, but got an error message saying "ffmpeg: unrecognized option '-hq'"

Thanks, I'm liking ubuntu so far.

---

