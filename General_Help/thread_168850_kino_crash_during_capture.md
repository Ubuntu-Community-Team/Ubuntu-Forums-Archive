---
title: "kino crash during capture"
date: 2006-05-01
forum: General Help
---

### Post by faflu on 2006-05-01
Hi all,

When I try to capture a film from my dv camera to Kino 8.0 the program crashes just upon pressing 'capture' button. Here's a dump of messages I receive:

>>> Audio Filter: FFMPEG Dub
> setting video preview size to 360x270
>> Starting Editor
>> Kino Common newFile
>> Creating undo/redo buffer
>>> Received playlist to store at position 0
>>>> Adding to end
>> on_main_window_map_event
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Enabled
>>> Using raw1394 capture
>>> AVC enabled
>> Constructing File Capture tracker
>> AV/C Disabled
>>> Trying /filmy/stycze&#324;2006/kamera001.avi
>>>> Registering /filmy/stycze&#324;2006/kamera001.avi with the tracker

Kino experienced a segmentation fault.
Dumping stack from the offending thread

Obtained 10 stack frames.
kino(__gxx_personality_v0+0x33e) [0x80740f2]
[0xffffe420]
kino(_ZN8AVI2File10WriteFrameERK5Frame+0x26f) [0x80a973d]
kino(_ZN10AVIHandler5WriteERK5Frame+0x1f) [0x809f621]
kino(_ZN11FileHandler10WriteFrameERK5Frame+0x99) [0x80a0897]
kino(_ZN11PageCapture12startCaptureEv+0x67f) [0x80ce597]
kino(startCapture+0x1b) [0x80f93af]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x43) [0xb776dab3]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x11e) [0xb77623a8]
/usr/lib/libgobject-2.0.so.0 [0xb7770b13]

Done dumping - exiting.

I run on Duron 800, nvidia GForce 4 MX 4000 AGP, Breezy Badger, kernel 2.6.12-10-386. Camera is JVC GR-D240E. For capturing I use iee1394.
Thanks for any suggestion.

---

