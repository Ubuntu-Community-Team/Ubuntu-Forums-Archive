---
title: "techsmith playback in mplayer"
date: 2010-07-18
forum: General Help
---

### Post by Coder68 on 2010-07-18
I spend hours following a dozen different how tos to get wma, asf, and a techsmtih videos to play.

I still can't play asf, or techsmith. The asf plays the video, but there is no audio.  The Techsmith flashes the video every so often but the sound works fine.

mplayer -vc help says the techsmith codec is working, but it is not.

Available video codecs:
vc:         vfm:      status:   info:  [lib/dll]
ffmvi1      ffmpeg    working   FFmpeg Motion Pixels  [motionpixels]
ffmdec      ffmpeg    working   FFmpeg Sony PlayStation MDEC (Motion DECoder)  [mdec]
ffsiff      ffmpeg    working   FFmpeg Beam Software SIFF  [vb]
ffmimic     ffmpeg    working   FFmpeg Mimic video  [mimic]
ffkmvc      ffmpeg    working   FFmpeg Karl Morton Video Codec  [kmvc]
ffzmbv      ffmpeg    working   FFmpeg Zip Motion-Block Video  [zmbv]
zmbv        vfw       working   Zip Motion-Block Video  [zmbv.dll]
yuv8        vfwex     working   YUV422 = Cb0 Y0 Cr0 Y1 Cb1 Y2 Cr1 Y3 (U Y V Y U Y V Y)  [kdvyuv8.dll]
blackmagic  vfw       working   Blackmagic 10-bit  [BMDCodecLib.dll]
mpegpes     mpegpes   working   MPEG-PES output (.mpg or DXR3/IVTV/DVB/V4L2 card)
ffmpeg1     ffmpeg    working   FFmpeg MPEG-1  [mpeg1video]
ffmpeg2     ffmpeg    working   FFmpeg MPEG-2  [mpeg2video]
ffmpeg12    ffmpeg    working   FFmpeg MPEG-1/2  [mpegvideo]
mpeg12      libmpeg2  working   MPEG-1 or 2 (libmpeg2)
ffmpeg12mc  ffmpeg    problems  FFmpeg MPEG-1/2 (XvMC)  [mpegvideo_xvmc]
ffmpeg12vdpau ffmpeg    working   FFmpeg MPEG-1/2 (VDPAU)  [mpegvideo_vdpau]
ffnuv       ffmpeg    working   NuppelVideo  [nuv]
ffbmp       ffmpeg    working   FFmpeg BMP  [bmp]
ffgif       ffmpeg    working   FFmpeg GIF  [gif]
fftiff      ffmpeg    working   FFmpeg TIFF  [tiff]
ffpcx       ffmpeg    working   FFmpeg PCX  [pcx]
ffpng       ffmpeg    working   FFmpeg PNG  [png]
mpng        mpng      working   PNG image  [libpng]
ffptx       ffmpeg    working   FFmpeg V.Flash PTX  [ptx]
fftga       ffmpeg    untested  FFmpeg TGA  [targa]
mtga        mtga      working   TGA image
sgi         sgi       working   SGI image
ffsunras    ffmpeg    working   FFmpeg SUN Rasterfile  [sunrast]
ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
fffli       ffmpeg    working   Autodesk FLI/FLC Animation  [flic]
ffaasc      ffmpeg    working   Autodesk RLE  [aasc]
ffloco      ffmpeg    working   LOCO video  [loco]
ffqtrle     ffmpeg    working   QuickTime Animation (RLE)  [qtrle]
ffrpza      ffmpeg    working   QuickTime Apple Video  [rpza]
ffsmc       ffmpeg    working   Apple Graphics (SMC) codec  [smc]
ff8bps      ffmpeg    working   Planar RGB (Photoshop)  [8bps]
ffcyuv      ffmpeg    working   Creative YUV (libavcodec)  [cyuv]
ffmsrle     ffmpeg    working   Microsoft RLE  [msrle]
ffroqvideo  ffmpeg    working   Id RoQ File Video  [roqvideo]
lzo         lzo       working   LZO compressed  [liblzo]
theora      theora    working   Theora (free, reworked VP3)  [libtheora]
smartsight  vfw       working   Verint Video Manager  [SN4Codec.dll]
msuscls     vfw       working   MSU Screen Capture Lossless Codec  [SCLS.DLL]
wincam      vfw       working   wincam screen capture codec  [wcmv.dll]
cram        vfw       problems  Microsoft Video 1  [msvidc32.dll]
ffcvid      ffmpeg    working   FFmpeg Cinepak Video  [cinepak]
cvidvfw     vfw       working   Cinepak Video  [iccvid.dll]
huffyuv     vfw       problems  HuffYUV  [huffyuv.dll]
ffvideo1    ffmpeg    working   FFmpeg Microsoft Video 1  [msvideo1]
ffmszh      ffmpeg    working   FFmpeg AVImszh  [mszh]
ffzlib      ffmpeg    working   FFmpeg AVIzlib  [zlib]
cvidxa      xanim     problems  XAnim's Radius Cinepak Video  [vid_cvid.xa]
ffhuffyuv   ffmpeg    working   FFmpeg HuffYUV  [huffyuv]
ffv1        ffmpeg    working   FFV1 (lossless codec)  [ffv1]
ffsnow      ffmpeg    working   FFSNOW (Michael's wavelet codec)  [snow]
ffasv1      ffmpeg    working   FFmpeg ASUS V1  [asv1]
ffasv2      ffmpeg    working   FFmpeg ASUS V2  [asv2]
ffvcr1      ffmpeg    working   FFmpeg ATI VCR1  [vcr1]
ffcljr      ffmpeg    working   FFmpeg Cirrus Logic AccuPak (CLJR)  [cljr]
ffsvq1      ffmpeg    working   FFmpeg Sorenson Video v1 (SVQ1)  [svq1]
ff4xm       ffmpeg    working   FFmpeg 4XM video  [4xm]
ffvixl      ffmpeg    working   Miro/Pinnacle VideoXL codec  [xl]
ffqtdrw     ffmpeg    working   FFmpeg QuickDraw  [qdraw]
ffindeo2    ffmpeg    working   FFmpeg Indeo 2  [indeo2]
ffflv       ffmpeg    working   FFmpeg Flash video  [flv]
fffsv       ffmpeg    working   FFmpeg Flash Screen video  [flashsv]
ffdivx      ffmpeg    working   FFmpeg DivX ;-) (MSMPEG-4 v3)  [msmpeg4]
ffmp42      ffmpeg    working   FFmpeg MSMPEG-4 v2  [msmpeg4v2]
ffmp41      ffmpeg    working   FFmpeg MSMPEG-4 v1  [msmpeg4v1]
ffwmv1      ffmpeg    working   FFmpeg WMV1/WMV7  [wmv1]
ffwmv2      ffmpeg    working   FFmpeg WMV2/WMV8  [wmv2]
ffwmv3      ffmpeg    problems  FFmpeg WMV3/WMV9  [wmv3]
ffwmv3vdpau ffmpeg    problems  FFmpeg WMV3/WMV9 (VDPAU)  [wmv3_vdpau]
ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]
ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]
ffh264      ffmpeg    working   FFmpeg H.264  [h264]
ffh264vdpau ffmpeg    working   FFmpeg H.264 (VDPAU)  [h264_vdpau]
ffsvq3      ffmpeg    working   FFmpeg Sorenson Video v3 (SVQ3)  [svq3]
ffodivx     ffmpeg    working   FFmpeg MPEG-4  [mpeg4]
ffwv1f      ffmpeg    working   WV1F MPEG-4  [mpeg4]
fflibschroedinger ffmpeg    working   Dirac (through FFmpeg libschroedinger)  [libschroedinger]
fflibdirac  ffmpeg    working   Dirac (through FFmpeg libdirac)  [libdirac]
xvid        xvid      working   Xvid (MPEG-4)  [libxvidcore.a]
divx4vfw    vfw       problems  DivX4Windows-VFW  [divx.dll]
divxds      dshow     working   DivX ;-) (MSMPEG-4 v3)  [divx_c32.ax]
divx        vfw       working   DivX ;-) (MSMPEG-4 v3)  [divxc32.dll]
mpeg4ds     dshow     working   Microsoft MPEG-4 v1/v2  [mpg4ds32.ax]
mpeg4       vfw       working   Microsoft MPEG-4 v1/v2  [mpg4c32.dll]
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
wmv8        dshow     working   Windows Media Video 8  [wmv8ds32.ax]
wmv7        dshow     working   Windows Media Video 7  [wmvds32.ax]
wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]
gotomeeting dmo       working   GoToMeeting codec  [G2M.dll]
ubmp4       vfw       problems  UB Video MPEG-4  [ubvmp4d.dll]
geomp4      vfw       working   GeoVision Advanced MPEG-4  [GXAMP4.dll]
zrmjpeg     zrmjpeg   problems  Zoran MJPEG passthrough
ffmjpeg     ffmpeg    working   FFmpeg MJPEG  [mjpeg]
ffmjpegb    ffmpeg    working   FFmpeg MJPEG-B  [mjpegb]
ijpg        ijpg      working   Independent JPEG Group's codec  [libjpeg]
m3jpeg      vfw       working   Morgan Motion JPEG Codec  [m3jpeg32.dll]
mjpeg       vfw       working   MainConcept Motion JPEG  [mcmjpg32.dll]
avid        vfw       working   AVID Motion JPEG  [AvidAVICodec.dll]
LEAD        vfw       working   LEAD (M)JPEG  [LCodcCMP.dll]
acdsee      vfw       working   ACDSee mjpeg  [ACDV.dll]
imagepower  vfw       problems  ImagePower MJPEG2000  [jp2avi.dll]
m3jpeg2k    vfw       working   Morgan MJPEG2000  [m3jp2k32.dll]
m3jpegds    dshow     crashing  Morgan MJPEG  [m3jpegdec.ax]
pegasusm    vfw       crashing  Pegasus Motion JPEG  [pvmjpg21.dll]
pegasusl    vfw       crashing  Pegasus lossless JPEG  [pvljpg20.dll]
pegasusmwv  vfw       crashing  Pegasus Motion Wavelet 2000  [pvwv220.dll]
frwuvfw     vfw       working   Forward Uncompressed Video Codec  [FRWU.dll]
frwdvfw     vfw       working   Forward JPEG Video Codec  [FRWD.dll]
frwtvfw     vfw       working   Forward JPEG+Alpha Video  [FRWT.dll]
vivo        vfw       working   Vivo H.263  [ivvideo.dll]
u263        dshow     working   UB Video H.263/H.263+/H.263++  [ubv263d+.ax]
i263        vfw       working   I263  [i263_32.drv]
ffi263      ffmpeg    working   FFmpeg I263  [h263i]
ffh263      ffmpeg    working   FFmpeg H.263+  [h263]
ffzygo      ffmpeg    untested  FFmpeg ZyGo  [h263]
h263xa      xanim     crashing  XAnim's CCITT H.263  [vid_h263.xa]
ffh261      ffmpeg    working   CCITT H.261  [h261]
qt261       qtvideo   working   QuickTime H.261 video  [QuickTime.qts]
h261xa      xanim     problems  XAnim's CCITT H.261  [vid_h261.xa]
m261        vfw       untested  M261  [msh261.drv]
indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]
ffdv        ffmpeg    working   FFmpeg DV  [dvvideo]
qdv         dshow     working   Sony Digital Video (DV)  [qdv.dll]
libdv       libdv     working   Raw DV (libdv)  [libdv.so.2]
mcdv        vfw       working   MainConcept DV Codec  [mcdvd_32.dll]
3ivXxa      xanim     working   XAnim's 3ivx Delta 3.5 plugin  [vid_3ivX.xa]
3ivX        dshow     working   3ivx Delta 4.5  [3ivxDSDecoder.ax]
rv3040      realvid   problems  Linux RealPlayer 10 RV30/40  [drvc.so]
rv3040win   realvid   working   Win32 RealPlayer 10 RV30/40  [drvc.dll]
rv40        realvid   problems  Linux RealPlayer 9 RV40  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40  [drvc.bundle/Contents/MacOS/drvc]
rv30        realvid   problems  Linux RealPlayer 8 RV30  [drv3.so.6.0]
rv30win     realvid   working   Win32 RealPlayer 8 RV30  [drv33260.dll]
rv30mac     realvid   working   Mac OS X RealPlayer 9 RV30  [drvc.bundle/Contents/MacOS/drvc]
ffrv20      ffmpeg    working   FFmpeg RV20  [rv20]
ffrv30      ffmpeg    problems  FFmpeg RV30  [rv30]
ffrv40      ffmpeg    working   FFmpeg RV40  [rv40]
rv20        realvid   problems  Linux RealPlayer 8 RV20  [drv2.so.6.0]
rv20winrp10 realvid   working   Win32 RealPlayer 10 RV20  [drv2.dll]
rv20win     realvid   working   Win32 RealPlayer 8 RV20  [drv23260.dll]
rv20mac     realvid   working   Mac OS X RealPlayer 9 RV20  [drv2.bundle/Contents/MacOS/drv2]
ffrv10      ffmpeg    working   FFmpeg RV10  [rv10]
alpary      dshow     working   Alparysoft lossless codec dshow  [aslcodec_dshow.dll]
alpary2     vfw       working   Alparysoft lossless codec vfw  [aslcodec_vfw.dll]
LEADMW20    dshow     working   Lead CMW wavelet 2.0  [LCODCCMW2E.dll]
lagarith    vfw       working   Lagarith Lossless Video Codec  [lagarith.dll]
psiv        vfw       working   Infinite Video PSI_V  [psiv.dll]
midivid3    vfw       working   [www.midivid.com/codec/mv3codec.html](www.midivid.com/codec/mv3codec.html)  [MV3.dll]
moyea       vfw       working   Moyea Flash to Video Converter  [MyFlashZip0.ax]
nsvideo     vfw       working   Power VideoWorks video  [nsvideo.dll]
smv2vfw     vfw       working   DideoNET SMV2  [smv2vfw.dll]
canopushq   vfw       working   Canopus HQ Codec  [CUVCcodc.dll]
canopusll   vfw       working   Canopus Lossless Codec  [CLLCcodc.dll]
ffvp3       ffmpeg    untested  FFmpeg VP3  [vp3]
fftheora    ffmpeg    untested  FFmpeg Theora  [theora]
vp3         vfwex     working   On2 Open Source VP3 Codec  [vp31vfw.dll]
vp4         vfwex     working   On2 VP4 Personal Codec  [vp4vfw.dll]
ffvp5       ffmpeg    working   FFmpeg VP5  [vp5]
vp5         vfwex     working   On2 VP5 Personal Codec  [vp5vfw.dll]
ffvp6       ffmpeg    working   FFmpeg VP6  [vp6]
ffvp6a      ffmpeg    untested  FFmpeg VP6A  [vp6a]
ffvp6f      ffmpeg    working   FFmpeg VP6 Flash  [vp6f]
vp6         vfwex     working   On2 VP6 Personal Codec  [vp6vfw.dll]
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]
mwv1        vfw       working   Motion Wavelets  [icmw_32.dll]
wavcvfw     vfw       working   centre for wavelets, approximation and infromation processing  [WavCWAIP.dll]
asv2        vfw       working   ASUS V2  [asusasv2.dll]
asv1        vfw       working   ASUS V1  [asusasvd.dll]
ffultimotion ffmpeg    working   FFmpeg IBM Ultimotion  [ultimotion]
ultimotion  vfw       working   IBM Ultimotion  [ultimo.dll]
mss1        dshow     working   Windows Screen Video  [msscds32.ax]
ucod        vfw       working   UCOD-ClearVideo  [clrviddd.dll]
vcr2        vfw       working   ATI VCR-2  [ativcr2.dll]
cjpg        vfw       working   Creative Labs Video Blaster Webcam  [CtWbJpg.DLL]
kensington  vfw       working   kensington webcam  [aoxdxipl.ax]
xjpg        vfw       working   xiricam Veo PC Camera  [camfc.dll]
ffduck      ffmpeg    working   Duck Truemotion1  [truemotion1]
fftm20      ffmpeg    working   FFmpeg Duck/On2 TrueMotion 2.0  [truemotion2]
tm20        dshow     working   TrueMotion 2.0  [tm20dec.ax]
sif1vfw     vfw       working   sif1 alpha4  [Sif1_vfw.dll]
sif1ds      dshow     problems  sif1 alpha4  [Sif1Dec.ax]
ffamv       ffmpeg    working   Modified MJPEG, used in AMV files  [amv]
ffsp5x      ffmpeg    working   SP5x codec - used by Aiptek MegaCam  [sp5x]
sp6x        vfw       problems  SP6x codec  [sp6x_32.dll]
sp5x        vfw       working   SP5x codec - used by Aiptek MegaCam  [sp5x_32.dll]
sp4x        vfw       working   SP4x codec - used by Aiptek MegaCam  [SP4X_32.DLL]
bt411       vfwex     working   Brooktree 411 codec  [btvvc32.drv]
bwmpeg      vfwex     working   Broadway MPEG Capture Codec  [bw10.dll]
zdsoft      vfwex     working   zdsoft screen recorder  [scrvid.dll]
webtrain    vfw       working   WebTrain Communication lossless screen recorder  [wtvc.dll]
xfire       vfw       working   xfire video  [xfcodec.dll]
vfapi       vfwex     untested  VFAPI rgb transcode codec  [VFCodec.dll]
eyecon      vfw       working   nokia eti camcorder eyecon  [nub2.dll]
smsvvfw     vfw       working   WorldConnect Wavelet Video  [wv32vfw.dll]
foxmotion   vfw       working   fox motion video  [fmcodec.dll]
tridvfw     vfw       untested  tridvfw  [TRICDC32.DRV]
vdtzvfw     vfw       working   Telegeny VDTZ  [VTZ32.DLL]
vivd2       vfw       working   SoftMedia ViVD V2 codec VfW  [ViVD2.dll]
winx        vfwex     working   Winnov Videum winx codec  [wnvwinx.dll]
ffwnv1      ffmpeg    working   FFmpeg wnv1 codec  [wnv1]
wnv1        vfwex     working   Winnov Videum wnv1 codec  [wnvplay1.dll]
vdom        vfw       working   VDOWave codec  [vdowave.drv]
vdowave3    vfw       working   VDOWave 3 advanced codec  [vdo32_30.drv]
lsv         vfw       working   Vianet Lsvx Video  [lsvxdec.dll]
ffvmnc      ffmpeg    working   FFmpeg VMware video  [vmnc]
vmnc        vfw       working   VMware video  [vmnc.dll]
ffsmkvid    ffmpeg    working   FFmpeg Smacker Video  [smackvid]
ffcavs      ffmpeg    working   Chinese AVS Video  [cavs]
ffdnxhd     ffmpeg    working   FFmpeg DNxHD  [dnxhd]
qt3ivx      qtvideo   working   win32/quicktime 3IV1 (3ivx)  [3ivx Delta 3.5.qtx]
qtactl      qtvideo   working   Win32/QuickTime Streambox ACT-L2  [ACTLComponent.qtx]
qtavui      qtvideo   working   Win32/QuickTime Avid Meridien Uncompressed  [AvidQTAVUICodec.qtx]
qth263      qtvideo   crashing  Win32/QuickTime H.263  [QuickTime.qts]
qtrlerpza   qtvideo   crashing  Win32/Quicktime RLE/RPZA  [QuickTime.qts]
qtvp3       qtvideo   crashing  Win32/QuickTime VP3  [On2_VP3.qtx]
qtzygo      qtvideo   problems  win32/quicktime ZyGo  [ZyGoVideo.qtx]
qtbhiv      qtvideo   untested  Win32/QuickTime BeHereiVideo  [BeHereiVideo.qtx]
qtcvid      qtvideo   working   Win32/QuickTime Cinepak  [QuickTime.qts]
qtindeo     qtvideo   crashing  Win32/QuickTime Indeo  [QuickTime.qts]
qtmjpeg     qtvideo   crashing  Win32/QuickTime MJPEG  [QuickTime.qts]
qtmpeg4     qtvideo   crashing  Win32/QuickTime MPEG-4  [QuickTime.qts]
qtsvq3      qtvideo   working   Win32/QuickTime SVQ3  [QuickTimeEssentials.qtx]
qtsvq1      qtvideo   problems  Win32/QuickTime SVQ1  [QuickTime.qts]
qtcine      qtvideo   working   cinewave uncompressed 10-bit codec  [CineWave.qtx]
vsslight    vfw       working   VSS Codec Light  [vsslight.dll]
vssh264     dshow     working   VSS H.264 New  [vsshdsd.dll]
vssh264old  vfw       working   VSS H.264 Old  [vssh264.dll]
vsswlt      vfw       working   VSS Wavelet Video Codec  [vsswlt.dll]
zlib        vfw       working   AVIzlib  [avizlib.dll]
mszh        vfw       working   AVImszh  [avimszh.dll]
alaris      vfwex     working   Alaris VideoGramPiX  [vgpix32d.dll]
vcr1        vfw       crashing  ATI VCR-1  [ativcr1.dll]
pim1        vfw       crashing  Pinnacle Hardware MPEG-1  [pclepim1.dll]
qpeg        vfw       working   Q-Team's QPEG ([www.q-team.de](www.q-team.de))  [qpeg32.dll]
rricm       vfw       crashing  rricm  [rricm.dll]
[COLOR=Red]_***ffcamtasia  ffmpeg    working   FFmpeg TechSmith Camtasia Screen Codec  [camtasia]***_[/COLOR]
camtasia    vfw       working   TechSmith Camtasia Screen Codec  [tsccvid.dll]
ffcamstudio ffmpeg    working   CamStudio Screen Codec  [camstudio]
fraps       vfw       working   FRAPS: Realtime Video Capture  [frapsvid.dll]
fffraps     ffmpeg    working   FFmpeg Fraps  [fraps]
fftiertexseq ffmpeg    working   FFmpeg Tiertex SEQ  [tiertexseqvideo]
ffvmd       ffmpeg    working   FFmpeg Sierra VMD video  [vmdvideo]
ffdxa       ffmpeg    working   FFmpeg Feeble Files DXA video  [dxa]
ffdsicinvideo ffmpeg    working   FFmpeg Delphine CIN video  [dsicinvideo]
ffthp       ffmpeg    working   FFmpeg THP video  [thp]
ffbfi       ffmpeg    working   FFmpeg BFI Video  [bfi]
ffbethsoftvid ffmpeg    problems  FFmpeg Bethesda Software VID  [bethsoftvid]
ffrl2       ffmpeg    working   FFmpeg RL2  [rl2]
fftxd       ffmpeg    working   FFmpeg Renderware TeXture Dictionary  [txd]
xan         vfw       working   XAN Video  [xanlib.dll]
ffwc3       ffmpeg    problems  FFmpeg XAN wc3  [xan_wc3]
ffidcin     ffmpeg    problems  FFmpeg Id CIN video  [idcinvideo]
ffinterplay ffmpeg    problems  FFmpeg Interplay Video  [interplayvideo]
ffvqa       ffmpeg    problems  FFmpeg VQA Video  [vqavideo]
ffc93       ffmpeg    problems  FFmpeg C93 Video  [c93]
rawrgb32    raw       working   RAW RGB32
rawrgb24    raw       working   RAW RGB24
rawrgb16    raw       working   RAW RGB16
rawbgr32flip raw       working   RAW BGR32
rawbgr32    raw       working   RAW BGR32
rawbgr24flip raw       working   RAW BGR24
rawbgr24    raw       working   RAW BGR24
rawbgr16flip raw       working   RAW BGR15
rawbgr16    raw       working   RAW BGR15
rawbgr15flip raw       working   RAW BGR15
rawbgr15    raw       working   RAW BGR15
rawbgr8flip raw       working   RAW BGR8
rawbgr8     raw       working   RAW BGR8
rawbgr1     raw       working   RAW BGR1
rawyuy2     raw       working   RAW YUY2
rawyuv2     raw       working   RAW YUV2
rawuyvy     raw       working   RAW UYVY
raw444P     raw       working   RAW 444P
raw422P     raw       working   RAW 422P
rawyv12     raw       working   RAW YV12
rawnv21     hmblck    working   RAW NV21
rawnv12     hmblck    working   RAW NV12
rawhm12     hmblck    working   RAW HM12
rawi420     raw       working   RAW I420
rawyvu9     raw       working   RAW YVU9
rawy800     raw       working   RAW Y8/Y800
null        null      crashing  NULL codec (no decoding!)


What gives?

Coder68

Playing back video should not be this damn hard. ](*,)

Coder68

---

### Post by andrew.46 on 2010-07-19
Hi Coder,

I will admit to not knowing a great deal about techsmith files but I have downloaded a sample file here:

[http://samples.mplayerhq.hu/V-codecs/tscc/TI_1_Einfuehrung.avi](http://samples.mplayerhq.hu/V-codecs/tscc/TI_1_Einfuehrung.avi)

and tested this file with the native decoder and the windows codec:

```

andrew@skamandros~$ mplayer -vc help | grep -i techsmith

ffcamtasia  ffmpeg    working   FFmpeg TechSmith Camtasia Screen Codec  [camtasia]
camtasia    vfw       working   TechSmith Camtasia Screen Codec  [tsccvid.dll]

```

I attach a screenshot of SMPlayer playing this file. Only catch is I am using the svn MPlayer, not the Ubuntu repository version...

Andrew

---

### Post by Coder68 on 2010-08-01
Still no joy.

After following a dozen more how to's (again), and two rebuilds, I gave up.  I installed a MS OS to play these files. Played them the first time without issue. Linux just does not play them worth a darn. :(  I get about 1 video image frame for every minute of black screen playback. (Even your link)  Absolutely useless.  It is just to dang hard to make these video files "just work".  For the time being, I will just have to keep a dual boot system for this laptop.

Coder68

---

### Post by luigi_mb on 2010-08-01
> **Coder68 said:**
> Still no joy.

After following a dozen more how to's (again), and two rebuilds, I gave up.  I installed a MS OS to play these files. Played them the first time without issue. Linux just does not play them worth a darn. :(  I get about 1 video image frame for every minute of black screen playback. (Even your link)  Absolutely useless.  It is just to dang hard to make these video files "just work".  For the time being, I will just have to keep a dual boot system for this laptop.

Coder68

I downloaded the sample suggested by andrew.46

[http://samples.mplayerhq.hu/V-codecs...infuehrung.avi](http://samples.mplayerhq.hu/V-codecs...infuehrung.avi)

and VLC is able to play it.


/luigi

---

### Post by andrew.46 on 2010-08-02
Hi Coder,

> **Coder68 said:**
> After following a dozen more how to's (again), and two rebuilds, I gave up.

If you are running Lucid perhaps try this guide I have just put together:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Andrew

---

