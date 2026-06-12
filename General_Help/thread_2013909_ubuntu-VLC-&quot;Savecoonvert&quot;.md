---
title: "ubuntu-VLC-&quot;Save/coonvert&quot;"
date: 2012-07-01
forum: General Help
---

### Post by Georgios1989 on 2012-07-01
p, li { white-space: pre-wrap; }I am new to linux and I had tried to convert from an original CD audio to Mp3 and I got this message. [COLOR=#000000]
[/COLOR]
 [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG I/II Layer 3.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 [COLOR=#000000]
[/COLOR]
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Can you helped me please![/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Thanks!
[/COLOR]

---

### Post by raja.genupula on 2012-07-01
open Synaptic and look for this [COLOR=#000000]"libavcodec" and check its installation . If installed then re-install else install it and try again with VLC .


Hope that helps :S 
[/COLOR]

---

### Post by ajgreeny on 2012-07-01
I don't think the standard libavcodec provides mp3 encoding, so to do that it may be easiest to enable the [medibuntu]("http://www.medibuntu.org/") repos and then replace **libavcodec52** with **libavcodec-extra-52**.

I am using 10.04 and the exact package names may have changed, but if you look for the extra vesions of all the libav* packages, you should be fine.

---

