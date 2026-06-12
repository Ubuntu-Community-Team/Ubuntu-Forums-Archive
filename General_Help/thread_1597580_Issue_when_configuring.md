---
title: "Issue when configuring?"
date: 2010-10-15
forum: General Help
---

### Post by Colo2 on 2010-10-15
Hello

I need to set up AirVideo server on my ubuntu machine

I followed this tutorial:

[http://wiki.birth-online.de/know-how/hardware/apple-iphone/airvideo-server-linux](http://wiki.birth-online.de/know-how/hardware/apple-iphone/airvideo-server-linux)

However, when it gets to the ./configure part. I get this:

> dump@STORAGE-DUMP:~/ffmpeg$ sudo ./configure --enable-pthreads --disable-shared --enable-static --enable-gpl --enable-libx264 --enable-libmp3lame --enable-libfaad --disable-decoder=aac
install prefix            /usr/local
source path               /home/dump/ffmpeg
C compiler                gcc
.align is power-of-two    no
ARCH                      x86 (generic)
big-endian                no
runtime cpu detection     no
yasm                      no
MMX enabled               yes
MMX2 enabled              yes
3DNow! enabled            yes
3DNow! extended enabled   yes
SSE enabled               yes
SSSE3 enabled             yes
CMOV enabled              no
CMOV is fast              no
EBX available             yes
EBP available             no
10 operands supported     yes
gprof enabled             no
debug symbols             yes
strip symbols             yes
optimizations             yes
static                    yes
shared                    no
postprocessing support    no
new filter support        no
filters using lavformat   no
network support           yes
threading support         pthreads
SDL support               no
Sun medialib support      no
AVISynth enabled          no
libdc1394 support         no
libdirac enabled          no
libfaac enabled           no
libfaad enabled           yes
libfaad dlopened          no
libgsm enabled            no
libmp3lame enabled        yes
libnut enabled            no
libopencore-amrnb support no
libopencore-amrwb support no
libopenjpeg enabled       no
libschroedinger enabled   no
libspeex enabled          no
libtheora enabled         no
libvorbis enabled         no
libx264 enabled           yes
libxvid enabled           no
zlib enabled              no
bzlib enabled             no

Enabled decoders:
aasc            eatgq            pcm_f32be
ac3            eatgv            pcm_f32le
adpcm_4xm        eatqi            pcm_f64be
adpcm_adx        eightbps        pcm_f64le
adpcm_ct        eightsvx_exp        pcm_mulaw
adpcm_ea        eightsvx_fib        pcm_s16be
adpcm_ea_maxis_xa    escape124        pcm_s16le
adpcm_ea_r1        ffv1            pcm_s16le_planar
adpcm_ea_r2        ffvhuff            pcm_s24be
adpcm_ea_r3        flac            pcm_s24daud
adpcm_ea_xas        flic            pcm_s24le
adpcm_g726        flv            pcm_s32be
adpcm_ima_amv        fourxm            pcm_s32le
adpcm_ima_dk3        fraps            pcm_s8
adpcm_ima_dk4        frwu            pcm_u16be
adpcm_ima_ea_eacs    gif            pcm_u16le
adpcm_ima_ea_sead    h261            pcm_u24be
adpcm_ima_iss        h263            pcm_u24le
adpcm_ima_qt        h263i            pcm_u32be
adpcm_ima_smjpeg    h264            pcm_u32le
adpcm_ima_wav        huffyuv            pcm_u8
adpcm_ima_ws        idcin            pcm_zork
adpcm_ms        iff_byterun1        pcx
adpcm_sbpro_2        iff_ilbm        pgm
adpcm_sbpro_3        imc            pgmyuv
adpcm_sbpro_4        indeo2            pgssub
adpcm_swf        indeo3            ppm
adpcm_thp        interplay_dpcm        ptx
adpcm_xa        interplay_video        qcelp
adpcm_yamaha        jpegls            qdm2
alac            kmvc            qdraw
als            libfaad            qpeg
amv            loco            qtrle
anm            mace3            r210
ape            mace6            ra_144
asv1            mdec            ra_288
asv2            mimic            rawvideo
atrac1            mjpeg            rl2
atrac3            mjpegb            roq
aura            mlp            roq_dpcm
aura2            mmvideo            rpza
avs            motionpixels        rv10
bethsoftvid        mp1            rv20
bfi            mp2            rv30
binkaudio_dct        mp3            rv40
binkaudio_rdft        mp3adu            sgi
bmp            mp3on4            shorten
c93            mpc7            sipr
cavs            mpc8            smackaud
cdgraphics        mpeg1video        smacker
cinepak            mpeg2video        smc
cljr            mpeg4            snow
cook            mpegvideo        sol_dpcm
cscd            msmpeg4v1        sonic
cyuv            msmpeg4v2        sp5x
dca            msmpeg4v3        sunrast
dnxhd            msrle            svq1
dpx            msvideo1        svq3
dsicinaudio        mszh            targa
dsicinvideo        nellymoser        theora
dvbsub            nuv            thp
dvdsub            pam            tiertexseqvideo
dvvideo            pbm            tiff
eac3            pcm_alaw        tmv
eacmv            pcm_bluray        truehd
eamad            pcm_dvd            truemotion1
truemotion2        vmdvideo        wmav1
truespeech        vmnc            wmav2
tta            vorbis            wmv1
twinvq            vp3            wmv2
txd            vp5            wmv3
ulti            vp6            wnv1
v210            vp6a            ws_snd1
v210x            vp6f            xan_dpcm
vb            vqa            xan_wc3
vc1            wavpack            xl
vcr1            wmapro            xsub
vmdaudio

Enabled encoders:
aac            ljpeg            pcm_u24le
ac3            mjpeg            pcm_u32be
adpcm_adx        mp2            pcm_u32le
adpcm_g726        mpeg1video        pcm_u8
adpcm_ima_qt        mpeg2video        pcm_zork
adpcm_ima_wav        mpeg4            pcx
adpcm_ms        msmpeg4v1        pgm
adpcm_swf        msmpeg4v2        pgmyuv
adpcm_yamaha        msmpeg4v3        ppm
alac            nellymoser        qtrle
asv1            pam            rawvideo
asv2            pbm            roq
bmp            pcm_alaw        roq_dpcm
dnxhd            pcm_f32be        rv10
dvbsub            pcm_f32le        rv20
dvdsub            pcm_f64be        sgi
dvvideo            pcm_f64le        snow
ffv1            pcm_mulaw        sonic
ffvhuff            pcm_s16be        sonic_ls
flac            pcm_s16le        svq1
flv            pcm_s24be        targa
gif            pcm_s24daud        tiff
h261            pcm_s24le        v210
h263            pcm_s32be        vorbis
h263p            pcm_s32le        wmav1
huffyuv            pcm_s8            wmav2
jpegls            pcm_u16be        wmv1
libmp3lame        pcm_u16le        wmv2
libx264            pcm_u24be        xsub

Enabled hwaccels:

Enabled parsers:
aac            dvdsub            mpeg4video
ac3            h261            mpegaudio
cavsvideo        h263            mpegvideo
dca            h264            pnm
dirac            mjpeg            vc1
dnxhd            mlp            vp3
dvbsub

Enabled demuxers:
aac            image2pipe        pcm_u16le
ac3            ingenient        pcm_u24be
aea            ipmovie            pcm_u24le
aiff            iss            pcm_u32be
amr            iv8            pcm_u32le
anm            lmlm4            pcm_u8
apc            m4v            pva
ape            matroska        qcp
asf            mjpeg            r3d
***            mlp            rawvideo
au            mm            rl2
avi            mmf            rm
avs            mov            roq
bethsoftvid        mp3            rpl
bfi            mpc            rtsp
bink            mpc8            sdp
c93            mpegps            segafilm
caf            mpegts            shorten
cavsvideo        mpegtsraw        siff
cdg            mpegvideo        smacker
daud            msnwc_tcp        sol
dirac            mtv            sox
dnxhd            mvi            str
dsicin            mxf            swf
dts            nc            thp
dv            nsv            tiertexseq
dxa            nut            tmv
ea            nuv            truehd
ea_cdata        ogg            tta
eac3            oma            txd
ffm            pcm_alaw        vc1
filmstrip        pcm_f32be        vc1t
flac            pcm_f32le        vmd
flic            pcm_f64be        voc
flv            pcm_f64le        vqf
fourxm            pcm_mulaw        w64
gsm            pcm_s16be        wav
gxf            pcm_s16le        wc3
h261            pcm_s24be        wsaud
h263            pcm_s24le        wsvqa
h264            pcm_s32be        wv
idcin            pcm_s32le        xa
iff            pcm_s8            yuv4mpegpipe
image2            pcm_u16be

Enabled muxers:
ac3            m4v            pcm_s16be
adts            matroska        pcm_s16le
aiff            matroska_audio        pcm_s24be
amr            mjpeg            pcm_s24le
asf            mlp            pcm_s32be
asf_stream        mmf            pcm_s32le
***            mov            pcm_s8
au            mp2            pcm_u16be
avi            mp3            pcm_u16le
avm2            mp4            pcm_u24be
crc            mpeg1system        pcm_u24le
daud            mpeg1vcd        pcm_u32be
dirac            mpeg1video        pcm_u32le
dnxhd            mpeg2dvd        pcm_u8
dts            mpeg2svcd        psp
dv            mpeg2video        rawvideo
eac3            mpeg2vob        rm
ffm            mpegts            roq
filmstrip        mpjpeg            rtp
flac            mxf            sox
flv            mxf_d10            spdif
framecrc        null            swf
gif            nut            tg2
gxf            ogg            tgp
h261            pcm_alaw        truehd
h263            pcm_f32be        vc1t
h264            pcm_f32le        voc
image2            pcm_f64be        wav
image2pipe        pcm_f64le        yuv4mpegpipe
ipod            pcm_mulaw

Enabled protocols:
file            pipe            tcp
gopher            rtmp            udp
http            rtp

Enabled filters:
crop            null            scale
format            nullsink        slicify
noformat        nullsrc            vflip

Enabled bsfs:
aac_adtstoasc        mjpega_dump_header    noise
dump_extradata        mov2textsub        remove_extradata
h264_mp4toannexb    mp3_header_compress    text2movsub
imx_dump_header        mp3_header_decompress

Enabled indevs:
dv1394            v4l            v4l2
oss

Enabled outdevs:
oss

License: GPL version 2 or later
Creating config.mak and config.h...
libavutil/avconfig.h is unchanged
dump@STORAGE-DUMP:~/ffmpeg$ 


I'm guessing that it hasn't worked?

The app doesn't seem to work, so I guess not.


Any ideas why this is?

I've tried setting the ffmpeg folder with full read/right permissions, and allowing execution.

I need this app, would hate to have to install windows just for this.:(

Thanks

Tom

---

### Post by TeoBigusGeekus on 2010-10-15
Type 
```
make
```
and press enter.
Then follow the rest of the tutorial.

---

### Post by WorMzy on 2010-10-15
I don't know why you've run ./configure with sudo, but if you get any errors with make, that may be why. Try removing the folder and starting again if that happens, and next time don't use sudo with configure.

---

### Post by Colo2 on 2010-10-15
Thank you both very much.

Combining your replies, I managed to fix it. 

For anyone else having the same problem:

I deleted FFMPEG, and ran ./configure again. That gave me the same error, so I just did "make" it took a while, but It finally worked

;) thanks

---

### Post by WorMzy on 2010-10-15
Just to clarify, you didn't get an error when you ran configure, it executed correctly and made the makefile with no problems. If you had gotten an error, you wouldn't be able to run make.

---

