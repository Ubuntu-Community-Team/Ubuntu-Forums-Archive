---
title: "Time-lapse photography post-processing."
date: 2011-09-19
forum: General Help
---

### Post by MG&amp;TL on 2011-09-19
I have a directory containing over 1050 small-ish Jpeg images that I want to convert to an mpeg to create a time-lapse movie. I understand I can use ffmpeg (?) but I need the images to be called image1, image2, etc. 

And Canon labels its images "IMG_5227.JPG" or similiar. How can I get around this? I have tried Phatch, but cannot work it out.

Any ideas? Thanks, people.

---

### Post by GWBouge on 2011-09-19
[http://ffmpeg.org/faq.html#SEC14]("http://ffmpeg.org/faq.html#SEC14")

They don't *have* to be named image1, image2, etc, they just have to follow a numerical sequence so ffmpeg knows what order they go in.  I'm not sure, however, if they have to start at 1 (or 001 or whatever).

---

### Post by MG&amp;TL on 2011-09-19
OK, thanks! I'll try that. :D I knew that there was an easy way of doing it, I just couldn't find it.

---

### Post by MG&amp;TL on 2011-09-19
The ffmpeg command seems to work fine, but the video player sticks around for ages and doesn't play anything, telling me it's streaming. Ideas?

---

### Post by FakeOutdoorsman on 2011-09-19
What's your ffmpeg command? What player are you using? Does it play fine with ffplay?

---

### Post by MG&amp;TL on 2011-09-19
Ah...I just double-click on it. I shall try ffplay. Reporting back in a mo...

---

### Post by MG&amp;TL on 2011-09-19
I err..."compiled" the MPEG with:

```
ffmpeg -f image2 -i IMG_6277.JPG ~/Desktop/Test.mpg
```

And ffplay crashes with:

```

[mpeg @ 0x10479a0] Format detected only with low score of 25, misdetection possible!
[mpeg @ 0x10479a0] Could not find codec parameters (Video: [0][0][0][0] / 0x0000)
Test.mpg: could not find codec parameters


```


??

---

### Post by FakeOutdoorsman on 2011-09-19
You told ffmpeg to make a movie out of one image. By default, the ffmpeg frame rate is 25 fps and I assume it attempted to make a movie that was 1/25 of a second long. I'm not sure if mpeg1 video or any players support such a short duration.

You can create a movie from a single image, but you need to add more options. You can loop the input indefinitely with the *-loop_input* option (renamed to *-loop* in recent ffmpeg). You can also give it an output duration with the *-t* option, such as *-t 10* for 10 seconds, or *-t 01:23:11.00* for 1 hour, 23 minutes, 11 seconds, 0 milliseconds. I'm guessing you don't want to make a movie from one image though.

How many images do you have? How long do you want your output video duration to be? Is there a certain format you want? Are your images numbered sequentially starting with one, such as IMG_0001.JPG, etc?

---

### Post by MG&amp;TL on 2011-09-19
I have 1050 images, starting with IMG_5227.JPG, and ending with IMG_6277.JPG.

What do I do then?

---

### Post by blueridgedog on 2011-09-19
What codecs do you have available?

```
ffmpeg -codecs
```

Then:

```
ffmpeg -f image2 -i IMG_6277.JPG -vcodec CODEC ~/Desktop/Test.mpg
```

Where CODEC is one from the list output with the first command marked by "E" for encoding.

Also, you may want to try to play your file with vlc.

---

### Post by blueridgedog on 2011-09-19
> **MG&TL said:**
> I have 1050 images, starting with IMG_5227.JPG, and ending with IMG_6277.JPG.

What do I do then?

From the docs:

```
ffmpeg -f image2 -i foo-%03d.jpeg -r 12 -s WxH foo.avi
The syntax foo-%03d.jpeg specifies to use a decimal number composed of three digits padded with zeroes to express the sequence number. It is the same syntax supported by the C printf function, but only formats accepting a normal integer are suitable.
```

and from the FAQ:

```
3.2 How do I encode single pictures into movies?

First, rename your pictures to follow a numerical sequence. For example, img1.jpg, img2.jpg, img3.jpg,... Then you may run:

  ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg
Notice that `%d' is replaced by the image number.

`img%03d.jpg' means the sequence `img001.jpg', `img002.jpg', etc...

If you have large number of pictures to rename, you can use the following command to ease the burden. The command, using the bourne shell syntax, symbolically links all files in the current directory that match *jpg to the `/tmp' directory in the sequence of `img001.jpg', `img002.jpg' and so on.

  x=1; for i in *jpg; do counter=$(printf %03d $x); ln -s "$i" /tmp/img"$counter".jpg; x=$(($x+1)); done
If you want to sequence them by oldest modified first, substitute $(ls -r -t *jpg) in place of *jpg.

Then run:

  ffmpeg -f image2 -i /tmp/img%03d.jpg /tmp/a.mpg
The same logic is used for any image format that ffmpeg reads.
```

---

### Post by FakeOutdoorsman on 2011-09-19
You can either rename all of your images or you could attempt to "pipe" the images to ffmpeg with "cat". It doesn't always work for me though such as images not in order. First open a terminal and navigate to the directory containing your images:
```
cat *.JPG | ffmpeg -f image2pipe -vcodec mjpeg -i - -qscale 4 output.mpg
```
So you have 1050 images? Using default settings I guess this will create a 42 second output. I'm not sure what format you want or how you're planning on using the movie, so I went with a simple output format.

If it doesn't work then you will have to rename your images. There are probably several graphical renamers out there or some good command-line scripts to do that task.

---

### Post by MG&amp;TL on 2011-09-19
Codecs:

```
ffmpeg version 0.7.1-4:0.7.1-3ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Aug 26 2011 10:12:01 with gcc 4.6.1
  configuration: --extra-version='4:0.7.1-3ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.1.0ubuntu2' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  avcodec     configuration: --extra-version='4:0.7.1.0ubuntu2' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
Codecs:
 D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec
 ..S... = Subtitle codec
 ...S.. = Supports draw_horiz_band
 ....D. = Supports direct rendering method 1
 .....T = Supports weird frame truncation
 ------
 D V D  4xm             4X Movie
 D V D  8bps            QuickTime 8BPS video
 D A    8svx_exp        8SVX exponential
 D A    8svx_fib        8SVX fibonacci
 D V D  FRWU            Forward Uncompressed
  EV    a64multi        Multicolor charset for Commodore 64
  EV    a64multi5       Multicolor charset for Commodore 64, extended with 5th color (colram)
 DEA    aac             Advanced Audio Coding
 D A    aac_latm        AAC LATM (Advanced Audio Codec LATM syntax)
 D V D  aasc            Autodesk RLE
 DEA    ac3             ATSC A/52A (AC-3)
  EA    ac3_fixed       ATSC A/52A (AC-3)
 D A    adpcm_4xm       ADPCM 4X Movie
 DEA    adpcm_adx       SEGA CRI ADX ADPCM
 D A    adpcm_ct        ADPCM Creative Technology
 D A    adpcm_ea        ADPCM Electronic Arts
 D A    adpcm_ea_maxis_xa ADPCM Electronic Arts Maxis CDROM XA
 D A    adpcm_ea_r1     ADPCM Electronic Arts R1
 D A    adpcm_ea_r2     ADPCM Electronic Arts R2
 D A    adpcm_ea_r3     ADPCM Electronic Arts R3
 D A    adpcm_ea_xas    ADPCM Electronic Arts XAS
 D A    adpcm_ima_amv   ADPCM IMA AMV
 D A    adpcm_ima_dk3   ADPCM IMA Duck DK3
 D A    adpcm_ima_dk4   ADPCM IMA Duck DK4
 D A    adpcm_ima_ea_eacs ADPCM IMA Electronic Arts EACS
 D A    adpcm_ima_ea_sead ADPCM IMA Electronic Arts SEAD
 D A    adpcm_ima_iss   ADPCM IMA Funcom ISS
 DEA    adpcm_ima_qt    ADPCM IMA QuickTime
 D A    adpcm_ima_smjpeg ADPCM IMA Loki SDL MJPEG
 DEA    adpcm_ima_wav   ADPCM IMA WAV
 D A    adpcm_ima_ws    ADPCM IMA Westwood
 DEA    adpcm_ms        ADPCM Microsoft
 D A    adpcm_sbpro_2   ADPCM Sound Blaster Pro 2-bit
 D A    adpcm_sbpro_3   ADPCM Sound Blaster Pro 2.6-bit
 D A    adpcm_sbpro_4   ADPCM Sound Blaster Pro 4-bit
 DEA    adpcm_swf       ADPCM Shockwave Flash
 D A    adpcm_thp       ADPCM Nintendo Gamecube THP
 D A    adpcm_xa        ADPCM CDROM XA
 DEA    adpcm_yamaha    ADPCM Yamaha
 DEA    alac            ALAC (Apple Lossless Audio Codec)
 D A    als             MPEG-4 Audio Lossless Coding (ALS)
 D A    amrnb           Adaptive Multi-Rate NarrowBand
 D A    amrwb           Adaptive Multi-Rate WideBand
 D V    amv             AMV Video
 D V D  anm             Deluxe Paint Animation
 D V D  ansi            ASCII/ANSI art
 D A    ape             Monkey's Audio
 DES    ***             Advanced SubStation Alpha subtitle
 DEV D  asv1            ASUS V1
 DEV D  asv2            ASUS V2
 D A    atrac1          Atrac 1 (Adaptive TRansform Acoustic Coding)
 D A    atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
 D V D  aura            Auravision AURA
 D V D  aura2           Auravision Aura 2
 D V D  avs             AVS (Audio Video Standard) video
 D V D  bethsoftvid     Bethesda VID video
 D V D  bfi             Brute Force & Ignorance
 D A    binkaudio_dct   Bink Audio (DCT)
 D A    binkaudio_rdft  Bink Audio (RDFT)
 D V    binkvideo       Bink video
 DEV D  bmp             BMP image
 D V D  c93             Interplay C93
 D V D  camstudio       CamStudio
 D V D  camtasia        TechSmith Screen Capture Codec
 D V D  cavs            Chinese AVS video (AVS1-P2, JiZhun profile)
 D V D  cdgraphics      CD Graphics video
 D V D  cinepak         Cinepak
 D V D  cljr            Cirrus Logic AccuPak
 D A    cook            COOK
 D V D  cyuv            Creative YUV (CYUV)
 D A    dca             DCA (DTS Coherent Acoustics)
 D V D  dfa             Chronomaster DFA
 DEV D  dnxhd           VC3/DNxHD
 DEV    dpx             DPX image
 D A    dsicinaudio     Delphine Software International CIN audio
 D V D  dsicinvideo     Delphine Software International CIN video
 DES    dvbsub          DVB subtitles
 DES    dvdsub          DVD subtitles
 DEV D  dvvideo         DV (Digital Video)
 D V D  dxa             Feeble Files/ScummVM DXA
 DEA    eac3            ATSC A/52 E-AC-3
 D V D  eacmv           Electronic Arts CMV video
 D V D  eamad           Electronic Arts Madcow Video
 D V D  eatgq           Electronic Arts TGQ video
 D V    eatgv           Electronic Arts TGV video
 D V D  eatqi           Electronic Arts TQI Video
 D V D  escape124       Escape 124
 DEV D  ffv1            FFmpeg video codec #1
 DEVSD  ffvhuff         Huffyuv FFmpeg variant
 DEA    flac            FLAC (Free Lossless Audio Codec)
 DEV D  flashsv         Flash Screen Video
 D V D  flic            Autodesk Animator Flic video
 DEVSD  flv             Flash Video (FLV) / Sorenson Spark / Sorenson H.263
 D V D  fraps           Fraps
 DEA    g722            G.722 ADPCM
 DEA    g726            G.726 ADPCM
 DEV D  gif             GIF (Graphics Interchange Format)
 D A    gsm             GSM
 D A    gsm_ms          GSM Microsoft variant
 DEV D  h261            H.261
 DEVSDT h263            H.263 / H.263-1996
 D VSD  h263i           Intel H.263
  EV    h263p           H.263+ / H.263-1998 / H.263 version 2
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 DEVSD  huffyuv         Huffyuv / HuffYUV
 D V D  idcinvideo      id Quake II CIN video
 D V D  iff_byterun1    IFF ByteRun1
 D V D  iff_ilbm        IFF ILBM
 D A    imc             IMC (Intel Music Coder)
 D V D  indeo2          Intel Indeo 2
 D V D  indeo3          Intel Indeo 3
 D V    indeo5          Intel Indeo Video Interactive 5
 D A    interplay_dpcm  DPCM Interplay
 D V D  interplayvideo  Interplay MVE video
 DEV D  jpegls          JPEG-LS
 D V D  jv              Bitmap Brothers JV video
 D V    kgv1            Kega Game Video
 D V D  kmvc            Karl Morton's video codec
 D V D  lagarith        Lagarith lossless
  EV    libdirac        libdirac Dirac 2.2
 DEA    libgsm          libgsm GSM
 DEA    libgsm_ms       libgsm GSM Microsoft variant
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
 D V D  libopenjpeg     OpenJPEG based JPEG 2000 decoder
 DEV    libschroedinger libschroedinger Dirac 2.2
 D A    libspeex        libspeex Speex
  EV    libtheora       libtheora Theora
  EA    libvorbis       libvorbis Vorbis
 DEV    libvpx          libvpx VP8
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libxvid         libxvidcore MPEG-4 part 2
  EV    ljpeg           Lossless JPEG
 D V D  loco            LOCO
 D A    mace3           MACE (Macintosh Audio Compression/Expansion) 3:1
 D A    mace6           MACE (Macintosh Audio Compression/Expansion) 6:1
 D V D  mdec            Sony PlayStation MDEC (Motion DECoder)
 D V D  mimic           Mimic
 DEV D  mjpeg           MJPEG (Motion JPEG)
 D V D  mjpegb          Apple MJPEG-B
 D A    mlp             MLP (Meridian Lossless Packing)
 D V D  mmvideo         American Laser Games MM Video
 D V D  motionpixels    Motion Pixels video
 D A    mp1             MP1 (MPEG audio layer 1)
 D A    mp1float        MP1 (MPEG audio layer 1)
 DEA    mp2             MP2 (MPEG audio layer 2)
 D A    mp2float        MP2 (MPEG audio layer 2)
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3adufloat     ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3float        MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 D A    mp3on4float     MP3onMP4
 D A    mpc7            Musepack SV7
 D A    mpc8            Musepack SV8
 DEVSDT mpeg1video      MPEG-1 video
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 DEVSDT mpeg2video      MPEG-2 video
 DEVSDT mpeg4           MPEG-4 part 2
 D V DT mpeg4_vdpau     MPEG-4 part 2 (VDPAU)
 D VSDT mpegvideo       MPEG-1 video
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D VSDT mpegvideo_xvmc  MPEG-1/2 video XvMC (X-Video Motion Compensation)
 DEVSD  msmpeg4         MPEG-4 part 2 Microsoft variant version 3
 D VSD  msmpeg4v1       MPEG-4 part 2 Microsoft variant version 1
 DEVSD  msmpeg4v2       MPEG-4 part 2 Microsoft variant version 2
 D V D  msrle           Microsoft RLE
 D V D  msvideo1        Microsoft Video 1
 D V D  mszh            LCL (LossLess Codec Library) MSZH
 D V D  mxpeg           Mobotix MxPEG video
 DEA    nellymoser      Nellymoser Asao
 D V D  nuv             NuppelVideo/RTJPEG
 DEV D  pam             PAM (Portable AnyMap) image
 DEV D  pbm             PBM (Portable BitMap) image
 DEA    pcm_alaw        PCM A-law
 D A    pcm_bluray      PCM signed 16|20|24-bit big-endian for Blu-ray media
 D A    pcm_dvd         PCM signed 20|24-bit big-endian
 DEA    pcm_f32be       PCM 32-bit floating point big-endian
 DEA    pcm_f32le       PCM 32-bit floating point little-endian
 DEA    pcm_f64be       PCM 64-bit floating point big-endian
 DEA    pcm_f64le       PCM 64-bit floating point little-endian
 D A    pcm_lxf         PCM signed 20-bit little-endian planar
 DEA    pcm_mulaw       PCM mu-law
 DEA    pcm_s16be       PCM signed 16-bit big-endian
 DEA    pcm_s16le       PCM signed 16-bit little-endian
 D A    pcm_s16le_planar PCM 16-bit little-endian planar
 DEA    pcm_s24be       PCM signed 24-bit big-endian
 DEA    pcm_s24daud     PCM D-Cinema audio signed 24-bit
 DEA    pcm_s24le       PCM signed 24-bit little-endian
 DEA    pcm_s32be       PCM signed 32-bit big-endian
 DEA    pcm_s32le       PCM signed 32-bit little-endian
 DEA    pcm_s8          PCM signed 8-bit
 DEA    pcm_u16be       PCM unsigned 16-bit big-endian
 DEA    pcm_u16le       PCM unsigned 16-bit little-endian
 DEA    pcm_u24be       PCM unsigned 24-bit big-endian
 DEA    pcm_u24le       PCM unsigned 24-bit little-endian
 DEA    pcm_u32be       PCM unsigned 32-bit big-endian
 DEA    pcm_u32le       PCM unsigned 32-bit little-endian
 DEA    pcm_u8          PCM unsigned 8-bit
 DEA    pcm_zork        PCM Zork
 DEV D  pcx             PC Paintbrush PCX image
 DEV D  pgm             PGM (Portable GrayMap) image
 DEV D  pgmyuv          PGMYUV (Portable GrayMap YUV) image
 D S    pgssub          HDMV Presentation Graphic Stream subtitles
 D V D  pictor          Pictor/PC Paint
 DEV D  png             PNG image
 DEV D  ppm             PPM (Portable PixelMap) image
 D V D  ptx             V.Flash PTX image
 D A    qcelp           QCELP / PureVoice
 D A    qdm2            QDesign Music Codec 2
 D V D  qdraw           Apple QuickDraw
 D V D  qpeg            Q-team QPEG
 DEV D  qtrle           QuickTime Animation (RLE) video
 D V D  r10k            AJA Kona 10-bit RGB Codec
 D V D  r210            Uncompressed RGB 10-bit
 DEV    rawvideo        raw video
 DEA    real_144        RealAudio 1.0 (14.4K) encoder
 D A    real_288        RealAudio 2.0 (28.8K)
 D V D  rl2             RL2 video
 DEA    roq_dpcm        id RoQ DPCM
 DEV D  roqvideo        id RoQ video
 D V D  rpza            QuickTime video (RPZA)
 DEV D  rv10            RealVideo 1.0
 DEV D  rv20            RealVideo 2.0
 D V D  rv30            RealVideo 3.0
 D V D  rv40            RealVideo 4.0
 D A    s302m           SMPTE 302M
 DEV    sgi             SGI image
 D A    shorten         Shorten
 D A    sipr            RealAudio SIPR / ACELP.NET
 D A    smackaud        Smacker audio
 D V D  smackvid        Smacker video
 D V D  smc             QuickTime Graphics (SMC)
 DEV D  snow            Snow
 D A    sol_dpcm        DPCM Sol
 D V D  sp5x            Sunplus JPEG (SP5X)
 D S    srt             SubRip subtitle
 D V D  sunrast         Sun Rasterfile image
 DEV D  svq1            Sorenson Vector Quantizer 1 / Sorenson Video 1 / SVQ1
 D VSD  svq3            Sorenson Vector Quantizer 3 / Sorenson Video 3 / SVQ3
 DEV D  targa           Truevision Targa image
 D VSD  theora          Theora
 D V D  thp             Nintendo Gamecube THP video
 D V D  tiertexseqvideo Tiertex Limited SEQ video
 DEV D  tiff            TIFF image
 D V D  tmv             8088flex TMV
 D A    truehd          TrueHD
 D V D  truemotion1     Duck TrueMotion 1.0
 D V D  truemotion2     Duck TrueMotion 2.0
 D A    truespeech      DSP Group TrueSpeech
 D A    tta             True Audio (TTA)
 D A    twinvq          VQF TwinVQ
 D V D  txd             Renderware TXD (TeXture Dictionary) image
 D V D  ultimotion      IBM UltiMotion
 DEV D  v210            Uncompressed 4:2:2 10-bit
 D V D  v210x           Uncompressed 4:2:2 10-bit
 D V    vb              Beam Software VB
 D V D  vc1             SMPTE VC-1
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  vcr1            ATI VCR1
 D A    vmdaudio        Sierra VMD audio
 D V D  vmdvideo        Sierra VMD video
 D V D  vmnc            VMware Screen Codec / VMware Video
 DEA    vorbis          Vorbis
 D VSD  vp3             On2 VP3
 D V D  vp5             On2 VP5
 D V D  vp6             On2 VP6
 D V D  vp6a            On2 VP6 (Flash version, with alpha channel)
 D V D  vp6f            On2 VP6 (Flash version)
 D V D  vp8             On2 VP8
 D V D  vqavideo        Westwood Studios VQA (Vector Quantized Animation) video
 D A    wavpack         WavPack
 D A    wmapro          Windows Media Audio 9 Professional
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 D A    wmavoice        Windows Media Audio Voice
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V D  wmv3            Windows Media Video 9
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
 D V D  wnv1            Winnov WNV1
 D A    ws_snd1         Westwood Audio (SND1)
 D A    xan_dpcm        DPCM Xan
 D V D  xan_wc3         Wing Commander III / Xan
 D V D  xan_wc4         Wing Commander IV / Xxan
 D V D  xl              Miro VideoXL
 DES    xsub            DivX subtitles (XSUB)
 D V    yop             Psygnosis YOP Video
 DEV D  zlib            LCL (LossLess Codec Library) ZLIB
 DEV D  zmbv            Zip Motion Blocks Video

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.

```


Thanks for extensive help guys (&gals?), I've never dabbled my toes in media before, so I don't have a clue what I'm doing...

---

### Post by blueridgedog on 2011-09-19
I don't think it is a codec issue...I think fakeoutdoorsman has it right...you did not give it enough images.

---

### Post by MG&amp;TL on 2011-09-19
The cat command is all good, :D but I get a random 'inteference' frame. roughly every 4 or 5 frames. Screenshot included.

I DO, however have a workable video apart from that. :D

---

### Post by JCM_Pico on 2011-09-19
convert -delay 20 -loop 0 *.jpg tlapse.gif
mencoder tlapse.gif -mf w=800:h=600:fps=25:type=gif -ovc lavc -lavcopts vcodec=mpeg4 -oac copy -o tlapse.avi


This works fine for me, but I make the gif converting in order to get a low size avi. If you are working with thousands of picture you may consider that

---

### Post by FakeOutdoorsman on 2011-09-19
> **MG&TL said:**
> The cat command is all good, :D but I get a random 'inteference' frame. roughly every 4 or 5 frames.
I guess cat isn't feeding the images in the correct order to ffmpeg, but I don't know how to correct that. So much for the lazy method. You'll have to rename the files. A quick search shows pyrenamer could be used to do this if you prefer something with a GUI, otherwise this [script](http://pastebin.com/X4gPBkiY) could be used. The FFmpeg FAQ also has a command you can try that blueridgedog already showed.

Whatever method you use should give you files numbered 1-1050. For example, if you end up with IMG_0001.JPG to IMG_1050.JPG then your command will look something like:
```
ffmpeg -i IMG_%04d.JPG -qscale 4 output.mpg
```

---

### Post by Sharpie1 on 2012-01-12
I use a program called Thunar to do my renaming, select all the files you want to rename then hit Edit ->Rename selecting the "Numbering" tab on the left of the dialog window that appears, "Name Only" in the box on the right and the number format either 001, 002, 003 for batches up to 1000 or 0001, 0002, 0003 for larger numbers. In the Ubuntu repo.

Sharpie1

---

### Post by fragos on 2012-01-12
You may be better served with Openshot which is a video editor which provides for input of numbered still images to create a video. The Openshot GUI is much more helpful and the ffmpeg CLI.

---

