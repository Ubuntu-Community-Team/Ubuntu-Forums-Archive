---
title: "removing library, not dependencies"
date: 2009-10-06
forum: General Help
---

### Post by fm1234 on 2009-10-06
I have two libavutil installed:

- libavutil-unstripped-50
- libavutil-unstripped-49****

which I suspect is making vlc not work properly to stream some Internet audio (I have another computer in which vlc works well, only with version -49).

How can I remove version -50 without having everything that depends on it also removed? (Synaptic wants to remove a lot of stuff including vlc).

TIA,
Fernando

---

### Post by mc4man on 2009-10-06
Some more details would be good. 

All ubuntu repo vlc's from intrepid thru karmic use version -49 of libavutil

so if you have a vlc (vlc-nox has the actual depend) that depends on -50 that I'd think it's from a ppa or you built it yourself

What version of vlc is giving you trouble? and is the same version working ok on another pc or is it a different version?

If 0.9.X works and 1.0.X doesn't then post command/errors or run 1.0.X from terminal to produce a debug
vlc -vv
or
 vlc -vv [COLOR="Blue"]command your using[/COLOR]

---

### Post by fm1234 on 2009-10-06
Hi,
I haven't put more info because I asked in the vlc forum for specific help with vlc and I came here for specific help with package/library management. 
Anyway, thanks for your offer. I think what happened is that an openshot installation screwed some libraries (or a mere addition of an incompatible version). I tried both vlc 1.?? before and now 0.9.9a (because it is working in another PC) with the same result.

As for the output, I hope it's ok to dump it here:

```

[00000407] main input debug: Creating an input for 'mms://stream2.rfm.pt/RFM?MSWMExt=.asf'
[00000407] main input debug: waiting for thread initialization
[00000407] main input debug: thread started
[00000407] main input debug: thread 2974808976 (input) created at priority 10 (input/input.c:370)
[00000407] main input debug: `mms://stream2.rfm.pt/RFM?MSWMExt=.asf' gives access `mms' demux `' path `stream2.rfm.pt/RFM?MSWMExt=.asf'
[00000407] main input debug: creating demux: access='mms' demux='' path='stream2.rfm.pt/RFM?MSWMExt=.asf'
[00000408] main demux debug: looking for access_demux module: 0 candidates
[00000408] main demux warning: no access_demux module matched "mms"
[00000408] main demux debug: TIMER module_Need() : 0.088 ms - Total 0.088 ms / 1 intvls (Avg 0.088 ms)
[00000407] main input debug: creating access 'mms' path='stream2.rfm.pt/RFM?MSWMExt=.asf'
[00000409] main access debug: looking for access module: 1 candidate
[00000409] access_mms access debug: waiting for connection...
[00000409] main access debug: net: connecting to stream2.rfm.pt port 1755
[00000409] main access debug: connection: Operation now in progress
[00000404] qt4 interface debug: Error while initializing qt-specific localization
[00000404] qt4 interface debug: Updating the stream status: 3
[00000409] main access warning: connection timed out
[00000409] access_mms access error: failed to open a connection (tcp)
[00000409] access_mms access debug: waiting for connection...
[00000409] main access debug: net: connecting to stream2.rfm.pt port 1755
[00000409] main access debug: connection: Operation now in progress
[00000409] main access warning: connection timed out
[00000409] access_mms access error: failed to open a connection (tcp)
[00000409] access_mms access error: cannot connect to server
[00000409] main access debug: net: connecting to stream2.rfm.pt port 80
[00000409] main access debug: connection: Operation now in progress
[00000409] main access debug: connection succeeded (socket = 12)
[00000409] access_mms access debug: HTTP reply 'HTTP/1.0 200 OK'
[00000409] access_mms access debug: stream type = broadcast
[00000409] access_mms access error: cannot read data 2
[00000409] access_mms access debug: complete header size=4948
[00000409] access_mms access debug: packet count=4294967295 packet size=1567
[00000409] access_mms access debug: starting stream
[00000409] main access debug: net: connecting to stream2.rfm.pt port 80
[00000409] main access debug: connection: Operation now in progress
[00000409] main access debug: connection succeeded (socket = 12)
[00000409] access_mms access debug: HTTP reply 'HTTP/1.0 200 OK'
[00000409] access_mms access debug: Content-Type: application/x-mms-framed
[00000409] access_mms access debug: Server: Cougar/9.5.6001.18161
[00000409] access_mms access debug: Date: Tue, 06 Oct 2009 18:44:24 GMT
[00000409] access_mms access debug: Pragma: no-cache, client-id=3660606507, xResetStrm=1, features="broadcast", AccelBW=0, AccelDuration=0, Speed=1.000
[00000409] access_mms access debug: Cache-Control: no-cache
[00000409] access_mms access debug: Last-Modified: Tue, 06 Oct 2009 18:44:24 GMT
[00000409] access_mms access debug: Supported: com.microsoft.wm.srvppair, com.microsoft.wm.sswitch, com.microsoft.wm.predstrm, com.microsoft.wm.fastcache, com.microsoft.wm.startupprofile
[00000409] access_mms access debug: Connection: keep-alive
[00000409] main access debug: using access module "access_mms"
[00000409] main access debug: TIMER module_Need() : 11155.460 ms - Total 11155.460 ms / 1 intvls (Avg 11155.459 ms)
[00000411] main stream debug: Using AStream*Stream
[00000411] main stream debug: pre-buffering...
[00000411] main stream debug: received first data for our buffer
[00000404] qt4 interface debug: New Event: type 1103
[00000404] qt4 interface debug: Updating the stream status: 2
[00000411] main stream debug: pre-buffering done 9402 bytes in 0s - 64 kbytes/s
[00000407] main input debug: creating demux: access='mms' demux='' path='stream2.rfm.pt/RFM?MSWMExt=.asf'
[00000412] main demux debug: looking for demux module: 60 candidates
[00000411] asf stream debug: found object guid: 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:4898
[00000411] asf stream debug: read "header object" subobj:6, reserved1:1, reserved2:2
[00000411] asf stream debug: found object guid: 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:32
[00000411] asf stream debug: read "stream bitrate properties object"
[00000411] asf stream debug:   - stream=1 bitrate=32600
[00000411] asf stream debug: found object guid: 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104
[00000411] asf stream debug: read "file properties object" file_id:0x4819ec6b-0x6ef7-0x43a9-0xa1f03a60f3bedf72 file_size:4948 creation_date:128935878887810000 data_packets_count:4294967295 play_duration:0 send_duration:0 preroll:2433 flags:9 min_data_packet_size:1567  max_data_packet_size:1567 max_bitrate:32600
[00000411] asf stream debug: found object guid: 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:4280
[00000411] asf stream debug: read "header extension object" reserved1:0xabd3d211-0xa9ba-0x11cf-0x8ee600c00c205365 reserved2:6 header_extension_size:4234
[00000411] asf stream debug: found object guid: 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:46
[00000411] asf stream debug: read "language list object" 2 entries
[00000411] asf stream debug:   - 'pt'
[00000411] asf stream debug:   - 'en-us'
[00000411] asf stream debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88
[00000411] asf stream debug: read "extended stream properties object":
[00000411] asf stream debug:   - start=0 end=0
[00000411] asf stream debug:   - data bitrate=32000 buffer=2433 initial fullness=0
[00000411] asf stream debug:   - alternate data bitrate=32000 buffer=2433 initial fullness=0
[00000411] asf stream debug:   - maximum object size=1536
[00000411] asf stream debug:   - flags=0x0
[00000411] asf stream debug:   - stream number=1 language=1
[00000411] asf stream debug:   - average time per frame=0
[00000411] asf stream debug:   - stream name count=0
[00000411] asf stream debug:   - payload extension system count=0
[00000411] asf stream debug: found object guid: 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26
[00000411] asf stream warning: unknown asf object (not loaded)
[00000411] asf stream debug: found object guid: 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:122
[00000411] asf stream debug: read "metadata object" 2 entries
[00000411] asf stream debug:   - IsVBR=0
[00000411] asf stream debug:   - DeviceConformanceTemplate=L2
[00000411] asf stream debug: found object guid: 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:3952
[00000411] asf stream warning: unknown asf object (not loaded)
[00000411] asf stream debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114
[00000411] asf stream debug: read "stream Properties object" stream_type:0xf8699e40-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0xbfc3cd50-0x618f-0x11cf-0x8bb200aa00b4e220 time_offset:0 type_specific_data_length:28 error_correction_data_length:8 flags:0x1 stream_number:1
[00000411] asf stream debug: found object guid: 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:164
[00000411] asf stream debug: read "extended content description object"
[00000411] asf stream debug:   - 'WMFSDKVersion' = '10.00.00.3708'
[00000411] asf stream debug:   - 'WMFSDKNeeded' = '0.0.0.0000'
[00000411] asf stream debug:   - 'IsVBR' = 'false'
[00000411] asf stream debug: found object guid: 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:174
[00000411] asf stream debug: read "codec list object" reserved_guid:0x86d15241-0x311d-0x11d0-0xa3a400a0c90348f6 codec_entries_count:1
[00000411] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9.1" description:" 32 kbps, 32 kHz, stereo 1-pass CBR" information_length:2
[00000411] asf stream debug: found object guid: 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:50
[00000411] asf stream debug: read "data object" file_id:0x4819ec6b-0x6ef7-0x43a9-0xa1f03a60f3bedf72 total data packet:0 reserved:257
[00000411] asf stream debug: + 'Unknown' GUID 0x0-0x0-0x0-0x0000000000000000 size:0pos:0
[00000411] asf stream debug:      + 'Header' GUID 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:4898pos:0
[00000411] asf stream debug:      |    + 'Stream Bitrate Properties' GUID 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:32pos:30
[00000411] asf stream debug:      |    + 'File Properties' GUID 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104pos:62
[00000411] asf stream debug:      |    + 'Header Extension' GUID 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:4280pos:166
[00000411] asf stream debug:      |    |    + 'Language List' GUID 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:46pos:212
[00000411] asf stream debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88pos:258
[00000411] asf stream debug:      |    |    + 'Unknown' GUID 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26pos:346
[00000411] asf stream debug:      |    |    + 'Metadata' GUID 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:122pos:372
[00000411] asf stream debug:      |    |    + 'Padding' GUID 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:3952pos:494
[00000411] asf stream debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114pos:4446
[00000411] asf stream debug:      |    + 'Extended content description' GUID 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:164pos:4560
[00000411] asf stream debug:      |    + 'Codec List' GUID 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:174pos:4724
[00000411] asf stream debug:      + 'Data' GUID 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:50pos:4898
[00000412] asf demux debug: found 1 streams
[00000407] main input debug: selecting program id=0
[00000412] asf demux debug: added new audio stream(codec:0x161,ID:1)
[00000412] main demux debug: using demux module "asf"
[00000412] main demux debug: TIMER module_Need() : 4469.286 ms - Total 4469.286 ms / 1 intvls (Avg 4469.286 ms)
[00000404] qt4 interface debug: New Event: type 1108
[00000414] main decoder debug: looking for decoder module: 30 candidates
[00000414] avcodec decoder debug: libavcodec initialized (interface 3412992 )
[00000414] avcodec decoder warning: Physical channel configuration not set : guessing
[00000414] avcodec decoder error: cannot open codec (Windows Media Audio 2)
[00000414] main decoder debug: TIMER module_Need() : 12.371 ms - Total 12.371 ms / 1 intvls (Avg 12.371 ms)
[00000414] main decoder error: no suitable decoder module for fourcc `wma2'.
VLC probably does not support this sound or video format.
[00000414] main decoder debug: killing decoder fourcc `wma2', 0 PES in FIFO
[00000409] access_mms access warning: unimplemented query in control
[00000407] main input debug: `mms://stream2.rfm.pt/RFM?MSWMExt=.asf' successfully opened
[00000407] main input debug: control type=1
[00000404] qt4 interface debug: New Event: type 1103
[00000404] qt4 interface debug: Updating the stream status: 3

```

---

### Post by mc4man on 2009-10-06
The ffmpeg libraries in the openshot ppa are borked, until fixed you should remove the ppa and all the libraries it installed
see here
[http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

There is a warning now on some openshot pages that notes this ( a bit late for some) and links to that thread to resolve

---

### Post by fm1234 on 2009-10-06
great! I'll try it.
Thanks,
Fernando

---

### Post by fm1234 on 2009-10-07
Yes it worked, thanks!

For the record, the correct thread link is:

[http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

Cheers,
Fernando

---

### Post by mc4man on 2009-10-07
> For the record, the correct thread link is

I've got to be more careful copy and pasting, or d. ck.

Glad you found the right one

---

