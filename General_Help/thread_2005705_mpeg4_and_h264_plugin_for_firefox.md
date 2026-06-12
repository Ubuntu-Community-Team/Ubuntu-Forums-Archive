---
title: "mpeg4 and h264 plugin for firefox?"
date: 2012-06-18
forum: General Help
---

### Post by qwertyjjj on 2012-06-18
What plugins do I have to install for the mpeg4 and h264 codecs to work on firefox?

---

### Post by idoitprone on 2012-06-18
> **qwertyjjj said:**
> What plugins do I have to install for the mpeg4 and h264 codecs to work on firefox?

here are the codecs
i am not sure h264 will be included

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

if that does not work then

you probably need the mozplugger  but it should be installed by deafult

---

### Post by qwertyjjj on 2012-06-18
> **idoitprone said:**
> here are the codecs
i am not sure h264 will be included

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

if that does not work then

you probably need the mozplugger  but it should be installed by deafult

tried that but still doesn't seem to work.
I can't find mozplugger in the add ons...how do I add it?

---

### Post by idoitprone on 2012-06-18
> **qwertyjjj said:**
> tried that but still doesn't seem to work.
I can't find mozplugger in the add ons...how do I add it?

it should be in the ubuntu repos

```
sudo apt-get install mozplugger
```

---

### Post by qwertyjjj on 2012-06-29
FF will still not play MPEG4 or H264, instead it forces an ascii file download and opens Libre Writer with this:

v=0
o=- 00001414312914925500 1150370773 IN IP4 192.168.0.10
s=RTSP Server(MPEG4) - OC8108195FF
c=IN IP4 0.0.0.0
t=0 0
a=charset:Shift_JIS
a=range:npt=0-
a=control:rtsp://192.168.0.10:554/img/media.sav?channel=2&ipaddr=192.168.0.10&port=&authinfo=
a=etag:1234567890
m=video 0 RTP/AVP 96
b=AS:3072
a=rtpmap:96 MP4V-ES/30000
a=control:trackID=1
a=fmtp:96 profile-level-id=1; config=000001B001000001B509000001000000012000845D4C28A021E0A31F;decode_buf=76800
a=x-framerate:20
a=framerate:20.0
m=audio 0 RTP/AVP 0
b=AS:64
a=rtpmap:0 PCMU/8000/1
a=control:trackID=2
a=ptime:125

---

### Post by kapetr on 2012-12-13
Firefox does not support h.264 yet.

Google: firefox html5 h.264

but ... there is experimental plugin - 
see [http://wildfox.sourceforge.net/](http://wildfox.sourceforge.net/)

(I didn't try it)

---

### Post by SeijiSensei on 2012-12-13
Install gecko-mediaplayer from the repositories.  It will launch mplayer and display the result within the browser window.

---

### Post by kapetr on 2012-12-17
> **SeijiSensei said:**
> Install gecko-mediaplayer from the repositories.  It will launch mplayer and display the result within the browser window.

Could you test the HTML5 integration here ?   :
[http://ie.microsoft.com/testdrive/graphics/videoformatsupport/default.html](http://ie.microsoft.com/testdrive/graphics/videoformatsupport/default.html)
[http://www.html5rocks.com/en/tutorials/video/basics/](http://www.html5rocks.com/en/tutorials/video/basics/)

---

### Post by ryankidman on 2012-12-17
I think not supported in Firefox try chrome or any other browser

---

### Post by SeijiSensei on 2012-12-17
> **kapetr said:**
> Could you test the HTML5 integration here ?   :
[http://ie.microsoft.com/testdrive/graphics/videoformatsupport/default.html](http://ie.microsoft.com/testdrive/graphics/videoformatsupport/default.html)

It plays the WebM verson. I didn't bother trying to install the UserAgentSwitcher plugin for Firefox to try and spoof my browser as IE, though.  I would imagine that Microsoft is not even-handed in tests like this.  They would naturally want to encode things in a way that doesn't work with browsers other than IE.

> [http://www.html5rocks.com/en/tutorials/video/basics/](http://www.html5rocks.com/en/tutorials/video/basics/)

I could play all the clips here.  I don't think Firefox invoked gecko-mediaplayer for any of them, of if it did, it played them within the page.

---

### Post by darkhole on 2013-10-27
Tight now Firefox support h.264 on Nightlies.
Check this information to enable it:
[http://askubuntu.com/questions/114872/how-can-i-get-h-264-support/366914#366914](http://askubuntu.com/questions/114872/how-can-i-get-h-264-support/366914#366914)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzU)

---

