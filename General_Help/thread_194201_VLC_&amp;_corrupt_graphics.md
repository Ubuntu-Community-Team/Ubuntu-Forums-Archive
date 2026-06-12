---
title: "VLC &amp; corrupt graphics"
date: 2006-06-11
forum: General Help
---

### Post by ajackson on 2006-06-11
Here is a strange one. When I use VLC to watch a file encoded with h264, the sound is ok but the picture is garbled (the file is fine because I've viewed it in other things). Now this was a known bug with the dapper version of VLC but was supposed to be fixed in version 0.8.4.debian-1ubuntu6, which is the version I have installed. Any ideas?

---

### Post by nab on 2006-06-11
I'm having also having a grapped picture in VLC (same version above). 
But I didn't test the file with other players :???: 

Here is the output of terminal:

```

vlc rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp VLC media player 0.8.4 Janus Sending request: OPTIONS rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp RTSP/1.0
CSeq: 1
User-Agent: VLC Media Player (LIVE555 Streaming Media v2005.10.05)


Received OPTIONS response: RTSP/1.0 200 OK
Server: QTSS/5.5.2 (Build/489.0.3; Platform/MacOSX; Release/Update; )
Cseq: 1
Public: DESCRIBE, SETUP, TEARDOWN, PLAY, PAUSE, OPTIONS, ANNOUNCE, RECORD


Sending request: DESCRIBE rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp RTSP/1.0
CSeq: 2
Accept: application/sdp
User-Agent: VLC Media Player (LIVE555 Streaming Media v2005.10.05)


Received DESCRIBE response: RTSP/1.0 200 OK
Server: QTSS/5.5.2 (Build/489.0.3; Platform/MacOSX; Release/Update; )
Cseq: 2
Cache-Control: no-cache
Content-length: 736
Date: Sun, 11 Jun 2006 10:15:01 GMT
Expires: Sun, 11 Jun 2006 10:15:01 GMT
Content-Type: application/sdp
x-Accept-Retransmit: our-retransmit
x-Accept-Dynamic-Rate: 1
Content-Base: rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp/


Need to read 736 extra bytes
Read 736 extra bytes: v=0
o=QTSS_Play_List 2974278780 3256737222 IN IP4 63.105.122.32
s=AFTVCartoonsH264500
c=IN IP4 0.0.0.0
b=AS:415
t=0 0
a=x-broadcastcontrol:RTSP
a=maxprate:53.000000
a=isma-compliance:2,2.0,2
a=control:*
m=video 0 RTP/AVP 96
b=AS:347
b=TIAS:335
a=maxprate:53
a=rtpmap:96 H264/90000
a=control:trackID=1
a=cliprect:0,0,480,640
a=framesize:96 640-480
a=fmtp:96 packetization-mode=1;profile-level-id=4D401E;sprop-parameter-sets=J01AHqkYFAe2ANQYBBrbegbAUF73wEA=,KM4JyA==
a=mpeg4-esid:201
m=audio 0 RTP/AVP 97
b=AS:78
b=TIAS:69
a=maxprate:43
a=rtpmap:97 mpeg4-generic/44100/2
a=control:trackID=2
a=fmtp:97 profile-level-id=15;mode=AAC-hbr;sizelength=13;indexlength=3;indexdeltalength=3;config=1210
a=mpeg4-esid:101

Sending request: SETUP rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp/trackID=1 RTSP/1.0
CSeq: 3
Transport: RTP/AVP/TCP;unicast;interleaved=0-1
User-Agent: VLC Media Player (LIVE555 Streaming Media v2005.10.05)


Received SETUP response: RTSP/1.0 200 OK
Server: QTSS/5.5.2 (Build/489.0.3; Platform/MacOSX; Release/Update; )
Cseq: 3
Cache-Control: no-cache
Session: 5010415192795937081
Date: Sun, 11 Jun 2006 10:15:01 GMT
Expires: Sun, 11 Jun 2006 10:15:01 GMT
Transport: RTP/AVP/TCP;unicast;interleaved=0-1


Sending request: SETUP rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp/trackID=2 RTSP/1.0
CSeq: 4
Transport: RTP/AVP/TCP;unicast;interleaved=2-3
Session: 5010415192795937081
User-Agent: VLC Media Player (LIVE555 Streaming Media v2005.10.05)


Received SETUP response: RTSP/1.0 200 OK
Server: QTSS/5.5.2 (Build/489.0.3; Platform/MacOSX; Release/Update; )
Cseq: 4
Session: 5010415192795937081
Cache-Control: no-cache
Date: Sun, 11 Jun 2006 10:15:01 GMT
Expires: Sun, 11 Jun 2006 10:15:01 GMT
Transport: RTP/AVP/TCP;unicast;interleaved=2-3


Sending request: PLAY rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp RTSP/1.0
CSeq: 5
Session: 5010415192795937081
Range: npt=0.000-
User-Agent: VLC Media Player (LIVE555 Streaming Media v2005.10.05)


Received PLAY response: RTSP/1.0 200 OK
Server: QTSS/5.5.2 (Build/489.0.3; Platform/MacOSX; Release/Update; )
Cseq: 5
Session: 5010415192795937081
Range: npt=now-
RTP-Info: url=rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp/trackID=1,url=rtsp://video1.multicasttech.com/AFTVCartoonsH264500.sdp/trackID=2


```

Can anybody direct me in the right direction?](*,) 
TIA

edit:
I tried updating to 0.8.5 from the videolan repros (deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /), but here vlc just chrashed everytime I tried to open a file or stream with "*** glibc detected *** free(): invalid pointer:...", so I moved back to the latetest version in the ubuntu repros.

Testing vlc with the mrk-file from [http://www.bunkus.org/videotools/mkvtoolnix/samples/vsshort-aac.mkv](http://www.bunkus.org/videotools/mkvtoolnix/samples/vsshort-aac.mkv) was working without a problem.

---

### Post by ajackson on 2006-06-13
No one else having problems with h264 files and vlc?
The file I am using to test it with is the one mentioned in the original bug report for this problem (sorry but I've lost the link to it).

Any ideas?

---

