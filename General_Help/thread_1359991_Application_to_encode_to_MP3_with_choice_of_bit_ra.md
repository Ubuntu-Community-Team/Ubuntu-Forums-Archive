---
title: "Application to encode to MP3 with choice of bit rate"
date: 2009-12-20
forum: General Help
---

### Post by alan_uk on 2009-12-20
I need to convert CDs (WAV) to MP3. However I also need to be able able to choose  between constant and variable bit rate mode, and Quality.  I have tried sound juicer but this does not give enough options. I will also need a batch facility.  What applications are available?

Thank you

Alan

---

### Post by rafalcieslak on 2009-12-20
Just use lame from command line.

```
usage: lame [options] <infile> [outfile]

    <infile> and/or <outfile> can be "-", which means stdin/stdout.

RECOMMENDED:
    lame -V2 input.wav output.mp3

OPTIONS:
    -b bitrate      set the bitrate, default 128 kbps
    -h              higher quality, but a little slower.  Recommended.
    -f              fast mode (lower quality)
    -V n            quality setting for VBR.  default n=4
                    0=high quality,bigger files. 9=smaller files
    --preset type   type must be "medium", "standard", "extreme", "insane",
                    or a value for an average desired bitrate and depending
                    on the value specified, appropriate quality settings will
                    be used.
                    "--preset help" gives more info on these

    --longhelp      full list of options

    --license       print License information

```

Hope that's what you are looking for ;)

---

### Post by MooPi on 2009-12-20
So alan_uk are you familiar with terminal and command line applications ? If so then the last post will work great for you. Let us know if you understand the interface.

---

### Post by pluto4ps on 2009-12-20
Use VLC...

---

### Post by pasti on 2009-12-20
I use SoundConverter it'll convert most formats into mp3 ogg etc, and you can select the quality & bitrate in the edit> preferences tab, although you do have to select/create a folder for the output there as well otherwise it'll dump the new file to where the last one was created, I haven't tried it with WAV as I rip my cd's as FLAC but it's converted every different format I've pointed it too including apple's ones, so give it a go

---

### Post by alan_uk on 2009-12-20
Thank you, the details given by way of the command line are the variables I need but I am not sure how to input them. I will give them a go

Thanks

Alan

---

