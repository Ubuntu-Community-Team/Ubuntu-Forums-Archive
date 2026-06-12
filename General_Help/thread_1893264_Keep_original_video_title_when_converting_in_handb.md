---
title: "Keep original video title when converting in handbrakeCLI"
date: 2011-12-09
forum: General Help
---

### Post by polardude1983 on 2011-12-09
So whenever I try to convert a video it renames the files to video.mp4

How do i keep the original title of the movie after conversion?

I asked in Ubuntu IRC and they said that HandbrakeCLI cannot do that. but i don't believe that.

Here is my code to convert my videos

```
HandBrakeCLI -i /home/christoph/Videos/ -o movie.mp4 --preset="iPhone & iPod Touch"

```

---

### Post by killermist on 2011-12-09
If Handbrake doesn't function as the documentation/help indicate, then a shell script may be the easiest fix.
```

#!/bin/bash
HandBrakeCLI -i "$1" -o video.mp4 --preset="iPhone & iPod Touch"
mv video.mp4 "$2"

```
Save as "brakewrap.sh" (or whatever you want) in ~/bin/ (or some other place in your path).  And use "brakewrap.sh source.mpg result.mp4"

---

### Post by polardude1983 on 2011-12-09
When I run the script you gave me in the test directory

```
HandBrakeCLI -i "$1" -o video.mp4 --preset="iPhone & iPod Touch"
```

I get this

```
Missing input device. Run HandBrakeCLI --help for syntax.
```


When I run this code from the Terminal

```
HandBrakeCLI -i /home/christoph/Videos/test/"$1" -o video.mp4 --preset="iPhone & iPod Touch"
```

I get this

```

christoph@christoph-desktop:~$ HandBrakeCLI -i /home/christoph/Videos/test"$1" -o video.mp4 --preset="iPhone & iPod Touch"
[21:35:12] hb_init: checking cpu count
[21:35:12] hb_init: starting libhb thread
HandBrake rev3736 (2011020499) - Linux i686 - http://handbrake.fr
2 CPUs detected
Opening /home/christoph/Videos/test...
[21:35:12] hb_scan: path=/home/christoph/Videos/test, title_index=1
libbluray/bdnav/index_parse.c:157: indx_parse(): error opening /home/christoph/Videos/test/BDMV/index.bdmv
libbluray/bluray.c:960: nav_get_title_list(/home/christoph/Videos/test) failed (0xaa6e9f0)
[21:35:12] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[21:35:12] dvd: not a dvd - trying as a stream/file instead
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xaa72d30] moov atom not found
[21:35:12] hb_stream_open: open /home/christoph/Videos/test/.mp4 failed
[21:35:12] libhb: scan thread found 0 valid title(s)
No title found.
HandBrake has exited.
christoph@christoph-desktop:~$ 

```

---

### Post by killermist on 2011-12-09
When used in a script, $1 and $2 (wrapped in quotes to save spaces in parameters/filenames) resolve to the first and second command line parameters passed to the script.

In the line you supplied initially, I assumed that you just omitted the filename from "/home/christoph/Videos/"

The whole goal of the script I wrote was to overcome the (assumed and anticipated) bad behavior of Handbrake.  If that can be bypassed more easily by actually passing a filename to Handbrake as part of the -i parameter, then that is the best solution.

---

### Post by polardude1983 on 2011-12-09
Sorry, What I'm wanting is to batch convert a bunch of videos in the test directory from whatever they are to mp4. but keep the original names.

Some of the videos in the test dir might be .mov or .avi. and I want them all converted to .mp4

---

### Post by killermist on 2011-12-09
Ah, then what you want may be:
```
for file in this.mpg that.mov something_else.avi  ; do HandBrakeCLI -i "$file" --preset="iPhone & iPod Touch"; done
```
If I recall, it'll drop the previous extension and retain the beginning of the filename followed by the new extension.

Try a "dry run" with just -i on a single file (preferably short/small to save time) and see what handbrake outputs.  That'll clue you in to what it'll output when fed multiple elements via the **for** loop I provided.

[edit]
The "for file in ..." part can take wild cards, so you can use "for file in *.{avi,mov,mpg}" to wildcard hit on all AVI, MOV or MPG files (pre-assuming they're all lower-case extensions and none are ".mpeg"  or whatever) or "for file in *" to just hit on everything (not sure if that will later hit on the newly created files coming into existence or not...)

I used for loops so often that I hadn't considered you must wanted to convert a whole directory.

[edit mk2]
It looks like Handbrake complains if you use -i without using -o.
```
killermist@killermist:/volumes/torrent-data/shared/music videos$ HandBrakeCLI -i Within\ Temptation\ -\ Ice\ Queen.mpg -o Within\ Temptation\ -\ Ice\ Queen.mp4 --preset="iPhone & iPod Touch"
[23:41:28] hb_init: checking cpu count
[23:41:28] hb_init: starting libhb thread
HandBrake rev3736 (2011011599) - Linux i686 - http://handbrake.fr
2 CPUs detected
Opening Within Temptation - Ice Queen.mpg...
[23:41:28] hb_scan: path=Within Temptation - Ice Queen.mpg, title_index=1
libbluray/bdnav/index_parse.c:157: indx_parse(): error opening Within Temptation - Ice Queen.mpg/BDMV/index.bdmv
libbluray/bluray.c:960: nav_get_title_list(Within Temptation - Ice Queen.mpg) failed (0x948d9d8)
[23:41:28] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[23:41:28] dvd: not a dvd - trying as a stream/file instead
Input #0, avi, from 'Within Temptation - Ice Queen.mpg':
  Duration: 00:04:16.73, start: 0.000000, bitrate: 898 kb/s
    Stream #0.0: Video: msmpeg4v1, yuv420p, 320x240, 23.97 tbr, 23.97 tbn, 23.97 tbc
    Stream #0.1: Audio: adpcm_ms, 22050 Hz, 1 channels, s16, 88 kb/s
[23:41:29] Channels reported by ffmpeg (1) != computed layout channels (2).
[23:41:29] scan: decoding previews for title 1
Scanning title 1...
[23:41:29] scan: 10 previews, 320x240, 23.970 fps, autocrop = 16/28/0/0, aspect 1.33:1, PAR 1:1
[23:41:29] scan: title (0) job->width:320, job->height:192
[23:41:29] libhb: scan thread found 1 valid title(s)
+ title 1:
  + stream: Within Temptation - Ice Queen.mpg
  + duration: 00:04:16
  + size: 320x240, pixel aspect: 1/1, display aspect: 1.33, 23.970 fps
  + autocrop: 16/28/0/0
  + chapters:
    + 1: cells 0->0, 0 blocks, duration 00:04:16
  + audio tracks:
    + 1, Unknown (ADPCM_M) (1.0 ch) (iso639-2: und)
  + subtitle tracks:
+ Using preset: iPhone & iPod Touch[23:41:29] 1 job(s) to process
[23:41:29] starting job
[23:41:29] work: sanitizing track 0 mixdown Dolby Pro Logic II to Mono
[23:41:29] work: sanitizing track 0 audio bitrate 128 to 96
[23:41:29] sync: expecting 6177 video frames
[23:41:29] work: only 1 chapter, disabling chapter markers
[23:41:29] job configuration:
[23:41:29]  * source
[23:41:29]    + Within Temptation - Ice Queen.mpg
[23:41:29]    + title 1, chapter(s) 1 to 1
[23:41:29]    + container: avi
[23:41:29]    + data rate: 898 kbps
[23:41:29]  * destination
[23:41:29]    + Within Temptation - Ice Queen.mp4
[23:41:29]    + container: MPEG-4 (.mp4 and .m4v)
[23:41:29]  * video track
[23:41:29]    + decoder: msmpeg4v1
[23:41:29]    + frame rate: same as source (around 23.970 fps)
[23:41:29]    + dimensions: 320 * 240 -> 320 * 192, crop 16/28/0/0, mod 0
[23:41:29]    + encoder: x264
[23:41:29]      + options: cabac=0:ref=2:me=umh:bframes=0:weightp=0:subme=6:8x8dct=0:trellis=0
[23:41:29]      + quality: 20.00 (RF)
[23:41:29]  * audio track 0
[23:41:29]    + decoder: Unknown (ADPCM_M) (1.0 ch) (track 1, id 1)
[23:41:29]    + mixdown: Mono
[23:41:29]    + encoder: faac
[23:41:29]      + bitrate: 96 kbps, samplerate: 22050 Hz
[23:41:29] encx264: min-keyint: auto (23), keyint: 240
[23:41:29] encx264: Encoding at constant RF 20.000000
x264 [info]: using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[23:41:29] reader: first SCR 0 id 1 DTS 0
x264 [info]: profile Constrained Baseline, level 1.2
Encoding: task 1 of 1, 97.47 % (114.94 fps, avg 101.98 fps, ETA 00h00m02s)[23:42:28] reader: done. 1 scr changes
Encoding: task 1 of 1, 98.70 % (117.10 fps, avg 102.28 fps, ETA 00h00m01s)[23:42:29] work: average encoding speed for job is 102.279243 fps
[23:42:29] sync: got 6098 frames, 6177 expected
Encoding: task 1 of 1, 98.70 % (117.10 fps, avg 102.28 fps, ETA 00h00m01s)[23:42:29] msmpeg4v1-decoder done: 6098 frames, 0 decoder errors, 0 drops
[23:42:29] render: lost time: 0 (0 frames)
[23:42:29] render: gained time: 0 (0 frames) (0 not accounted for)
x264 [info]: frame I:76    Avg QP:18.82  size:  6687  PSNR Mean Y:45.81 U:49.82 V:50.65 Avg:46.81 Global:46.07
x264 [info]: frame P:6022  Avg QP:21.15  size:  2048  PSNR Mean Y:42.89 U:45.63 V:46.93 Avg:43.71 Global:43.22
x264 [info]: mb I  I16..4: 20.1%  0.0% 79.9%
x264 [info]: mb P  I16..4:  3.8%  0.0%  8.1%  P16..4: 45.0% 17.0%  6.1%  0.0%  0.0%    skip:20.1%
x264 [info]: coded y,uvDC,uvAC intra: 68.7% 91.0% 62.6% inter: 28.1% 54.7% 7.9%
x264 [info]: i16 v,h,dc,p: 32% 26% 14% 28%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 25% 20% 18%  6%  7%  7%  6%  6%  5%
x264 [info]: i8c dc,h,v,p: 39% 23% 24% 14%
x264 [info]: ref P L0: 85.9% 14.1%
x264 [info]: SSIM Mean Y:0.9793589 (16.853db)
x264 [info]: PSNR Mean Y:42.924 U:45.678 V:46.974 Avg:43.751 Global:43.242 kb/s:400.07
[23:42:29] adpcm_ms-decoder done: 0 frames, 0 decoder errors, 0 drops
Muxing: this may take awhile...[23:42:30] mux: track 0, 6098 frames, 12836445 bytes, 399.99 kbps, fifo 8
[23:42:30] mux: track 1, 5528 frames, 1219478 bytes, 38.00 kbps, fifo 256
[23:42:30] libhb: work result = 0

Rip done!
HandBrake has exited.
```
```
-rw-r--r-- 1 killermist 999  14M Dec  9 23:42 Within Temptation - Ice Queen.mp4
-rw-r--r-- 1 killermist 999  28M Aug 29  2009 Within Temptation - Ice Queen.mpg
```

---

