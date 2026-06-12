---
title: "Downloading Stream from RTSP protocol"
date: 2010-10-11
forum: General Help
---

### Post by x53x6ex69x67x67x65x72 on 2010-10-11
Hi
I need to download a WMV video from RTSP protocol.
I tried mplayer ; It doesn't work.
According to this:
[http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm#recmp](http://all-streaming-media.com/record-video-stream/all-streaming-video-recording-software.htm#recmp)
I tried VLC but it doesn't work too (The link has two videos - first is intro and company logo and the second is the main video and VLC just shows first in low resolution!)
In Windows "NetTransport" Can get the stream (Both Videos separately) with high resolution.
I googled for a linux application and found these:
[http://bisqwit.iki.fi/source/ms-rtsp-dump/](http://bisqwit.iki.fi/source/ms-rtsp-dump/)
[http://sourceforge.net/projects/dget](http://sourceforge.net/projects/dget)
[http://sourceforge.net/projects/msdl/](http://sourceforge.net/projects/msdl/)

First & Second Ones dont work! Third works and gets stream with high resolution. but it just get the main video and doesn't download Intro video. It also has several bugs (Download percent ,Estimated Time,... and the most important its resume feature that writes bytes in the first of file instead of its end)

Do you know better application for downloading RTSP streaming videos (with full protocol support)?

Thanks

---

### Post by andrew.46 on 2010-10-11
Can you give the address of the stream?

Andrew

---

### Post by x53x6ex69x67x67x65x72 on 2010-10-12
Hi
rtsp://media1.iransima.ir/tv4/TV4_13890619_019.wmv

---

### Post by andrew.46 on 2010-10-12
Unfortunately I had very little luck with this stream, using both a recent vlc and the svn MPlayer. Hopefully somebody else can help out :(.

Andrew

---

