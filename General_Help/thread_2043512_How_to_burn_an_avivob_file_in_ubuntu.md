---
title: "How to burn an avi/vob file in ubuntu?"
date: 2012-08-16
forum: General Help
---

### Post by linux_dream on 2012-08-16
Hi guys,
I've been spending more than 5 hours today without any success on burning a simple DVD in order to watch it on my TV.
I've downloaded a movie in format .avi. Under Windows XP I converted it to .vob as I undertood that nero (old version at least) and brasero and other burning programs can only burn a .vob if I want the DVD to be readable on an external dvd player (for TV).
So now I have a movie.avi and movie.vob, the former is around 800 mb while the latter over 2 Gb.
I've downloaded several programs under ubuntu (the nero of windows XP failed at burning the movie.vob because "it was over 2 Gb"), namely brasero, k3b, DVD styler and probably another one I forgot.
I tried to burn the .vob in all of these programs but I always got some error.
In brasero I get the error that the file is over 2 Gb and that apparently it's the third version of ISO9660 and that probably I wouldn't be able to watch it on my TV.
The log file of brasero is ```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : Ocurrió un error interno (brasero_burn_record brasero-burn.c:2839)
```.
I bought my DVD burner yesterday so I don't think that's the problem.
In k3b I got the error that the vob file (that I put in the VIDEO_TS folder) isn't an appropriate file or something like that.
I've ran out of any ideas on how to burn the movie in order to watch it in my TV. Any help will be very appreciated.  Thank you in advance.


Edit: Log file of k3b: ```
  p, li { white-space: pre-wrap; }  [FONT=Monospace]Devices[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]TSSTcorp CDDVDW SH-222BB SB00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
  [FONT=Monospace]K3b::IsoImager[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]mkisofs print size result: 0 (0 bytes)[/FONT]
  [FONT=Monospace]System[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]K3b Version: 1.91.0[/FONT]
 [FONT=Monospace]KDE Version: 4.4.5 (KDE 4.4.5)[/FONT]
 [FONT=Monospace]QT Version:  4.6.2[/FONT]
 [FONT=Monospace]Kernel:      2.6.32-42-generic[/FONT]
  [FONT=Monospace]Used versions[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]mkisofs: 1.1.10[/FONT]
  [FONT=Monospace]mkisofs[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-isaac/k3bVideoDvd0/'.[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage: Unable to parse DVD-Video structures.[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.[/FONT]
 [FONT=Monospace]Possible reasons:[/FONT]
 [FONT=Monospace]  - VIDEO_TS subdirectory was not found on specified location[/FONT]
 [FONT=Monospace]  - VIDEO_TS has invalid contents[/FONT]
  [FONT=Monospace]mkisofs calculate size command:[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid lavidaloca -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-isaac/k3bYV1576.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-isaac/k3bnm1576.tmp -dvd-video -f /tmp/kde-isaac/k3bVideoDvd0[/FONT]
 [FONT=Monospace]
[/FONT]

```

---

### Post by cbraxton on 2012-08-16
Try the program "devede" which you can install from the repositories, this program makes it very easy to create simple DVDs from video files. I think the default is to output PAL format, so you'll need to change to select the NTSC option if you're in the U.S.

---

### Post by linux_dream on 2012-08-16
> **cbraxton said:**
> Try the program "devede" which you can install from the repositories, this program makes it very easy to create simple DVDs from video files. I think the default is to output PAL format, so you'll need to change to select the NTSC option if you're in the U.S.
Thanks. That worked. I created an ISO file from the movie.avi file. And then burned it with devede. I did not test it on the external dvd yet but at least it burned the dvd well, my computer can watch the movie.
And I stick with PAL (Argentina).

---

### Post by ads52 on 2012-08-17
Newer tvs are able to play a limited variety of media files directly from usb, I guess this is not the case with your tv? This gets around the whole transcoding issue...

---

### Post by linux_dream on 2012-08-17
> **ads52 said:**
> Newer tvs are able to play a limited variety of media files directly from usb, I guess this is not the case with your tv? This gets around the whole transcoding issue...
Yeah not the case of my TV (older than 10 years old). There's no info also on what my dvd player can read (The model is a Sanyo dvd player 9205), I could not find any manual nor any technical details on the internet. And I didn't buy it, but someone gave it to me as a present without any manual, etc).
Anyway that worked, I could watch the movie so thank you very much guys!

---

### Post by ads52 on 2012-08-18
Great news :). Mind you if you ever wanted to do the work by hand you can simply use the same tools that devede uses, but *without* the gui and with more control. I have just now finished writing the downloaded movie richard2.flv to dvd as follows:

Produce an mpeg2 stream using an FFmpeg preset:

```

ffmpeg -i richard2.flv \
       -target pal-dvd -aspect 16:9 output.mpg

```

FFmpeg has a small collection of these 'presets':

```

-target type (output)
      Specify target file type ("vcd", "svcd", "dvd", "dv", "dv50"). type may be
    prefixed with "pal-", "ntsc-" or "film-" to use the corresponding standard.
    All the format options (bitrate, codecs, buffer sizes) are then set
    automatically. You can just type:

            ffmpeg -i myfile.avi -target vcd /tmp/vcd.mpg

    Nevertheless you can specify additional options as long as you know they do
    not conflict with the standard, as in:

            ffmpeg -i myfile.avi -target vcd -bf 2 /tmp/vcd.mpg


```

Then create the dvd structure with dvdauthor:

```

dvdauthor -t -o dvd --video=pal -f output.mpg
dvdauthor -T -o dvd

```

A little oddity of the current dvdauthor is that you will need to write either 'PAL' or 'NTSC' (without the inverted commas) to the file *$HOME/.config/video_format*. Then create and burn the iso:

```

mkisofs -dvd-video -o richard2.iso dvd/
growisofs -dvd-compat -Z /dev/sr0=richard2.iso

```

Perhaps you may have to modify the target of */dev/sr0*. Works very nicely and is an old technique, ntsc users would need to modify it all slightly of course. Even if this only makes you appreciate what DeVeDe does for you :).

---

