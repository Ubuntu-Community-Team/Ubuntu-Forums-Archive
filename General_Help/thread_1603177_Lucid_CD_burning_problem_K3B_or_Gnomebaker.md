---
title: "Lucid CD burning problem K3B or Gnomebaker"
date: 2010-10-22
forum: General Help
---

### Post by Fazl on 2010-10-22
Hi all

I am having a problem in burning my CDrs. I can't! Whenever I try to burn a CD, it starts up and then gives OPC failure. This is the info from Gnomebake

scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
SCSI buffer size: 64512
Cdrecord-ProDVD-ProBD-Clone 3.00 (i686-pc-linux-gnu) Copyright (C) 1995-2010 Jörg Schilling
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'schily-0.9'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4242N'
Revision       : '0201'
Device seems to be: Generic mmc2 DVD-ROM.
Current: CD-R
Profile: DVD-ROM 
Profile: CD-ROM 
Profile: CD-R (current)
Profile: CD-RW 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1644048 = 1605 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Warning: Cannot read drive buffer.
cdrecord: Warning: The DMA speed test has been skipped.
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1605 K BSize: 1605 K
Starting new track at sector: 0
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:    7.455s
Average write speed 920.4x.
Fixating...
Fixating time:    0.006s
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
####################################################################
END  END  END  END  END  END  END  END  END  END  END  END  
###################################################################
I've also used Brasero and got this failure info

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///(2007)%20The%20Heart%20of%20Everything/06%20Hand%20of%20Sorrow.mp3
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/06%20Hand%20of%20Sorrow.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/06 Hand of Sorrow.mp3 at /(2007) The Heart of Everything/06 Hand of Sorrow.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/The%20Heart%20of%20Everything.jpg
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/The Heart of Everything.jpg at /(2007) The Heart of Everything/The Heart of Everything.jpg
BraseroBurnURI Information retrieval for burn:///(1998)%20The%20Dance/01%20The%20Dance.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1998) The Dance/01 The Dance.mp3 at /(1998) The Dance/01 The Dance.mp3
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/07%20Blooded.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/07 Blooded.mp3 at /(1997) Enter/07 Blooded.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/09%20All%20I%20Need.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/09 All I Need.mp3 at /(2007) The Heart of Everything/09 All I Need.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/07%20Deceiver%20of%20Fools.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/07 Deceiver of Fools.mp3 at /(2001) Mother Earth/07 Deceiver of Fools.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/11%20Forgiven.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/11 Forgiven.mp3 at /(2007) The Heart of Everything/11 Forgiven.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything
BraseroBurnURI Adding directory (null) at /(2007) The Heart of Everything/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/03 Frozen.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/11 Forgiven.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/10 The Truth Beneath The Rose.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/01 The Howling.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/The Heart of Everything.jpg
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/08 Final Destination.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/09 All I Need.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/04 Our Solemn Hour.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/05 The Heart of Everything.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/06 Hand of Sorrow.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/07 The Cross.mp3
BraseroBurnURI Graft already in list /(2007) The Heart of Everything/02 What Have You Done (feat. Keith Caputo).mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/05%20Pale.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/05 Pale.mp3 at /(2004) The Silent Force/05 Pale.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/01%20The%20Howling.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/01 The Howling.mp3 at /(2007) The Heart of Everything/01 The Howling.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/08%20Final%20Destination.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/08 Final Destination.mp3 at /(2007) The Heart of Everything/08 Final Destination.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/10%20It's%20the%20Fear.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/10 It's the Fear.mp3 at /(2004) The Silent Force/10 It's the Fear.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/12%20A%20Dangerous%20Mind.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/12 A Dangerous Mind.mp3 at /(2004) The Silent Force/12 A Dangerous Mind.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/09%20Dark%20Wings.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/09 Dark Wings.mp3 at /(2001) Mother Earth/09 Dark Wings.mp3
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/05%20Gatekeeper.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/05 Gatekeeper.mp3 at /(1997) Enter/05 Gatekeeper.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/09%20Aquarius.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/09 Aquarius.mp3 at /(2004) The Silent Force/09 Aquarius.mp3
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/02%20Enter.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/02 Enter.mp3 at /(1997) Enter/02 Enter.mp3
BraseroBurnURI Information retrieval for burn:///(1998)%20The%20Dance
BraseroBurnURI Adding directory (null) at /(1998) The Dance/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Graft already in list /(1998) The Dance/The Dance.jpg
BraseroBurnURI Graft already in list /(1998) The Dance/01 The Dance.mp3
BraseroBurnURI Graft already in list /(1998) The Dance/03 The Other Half (Of me).mp3
BraseroBurnURI Graft already in list /(1998) The Dance/02 Another Day.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force
BraseroBurnURI Adding directory (null) at /(2004) The Silent Force/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Graft already in list /(2004) The Silent Force/05 Pale.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/02 See Who I Am.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/13 The Swan Song.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/07 Angels.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/The Silent Force.jpg
BraseroBurnURI Graft already in list /(2004) The Silent Force/11 Somewhere.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/08 Memories.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/04 Stand My Ground.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/12 A Dangerous Mind.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/06 Forsaken.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/03 Jillian (I'd Give My Heart).mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/01 Intro.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/09 Aquarius.mp3
BraseroBurnURI Graft already in list /(2004) The Silent Force/10 It's the Fear.mp3
BraseroBurnURI Information retrieval for burn:///(1998)%20The%20Dance/03%20The%20Other%20Half%20(Of%20me).mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1998) The Dance/03 The Other Half (Of me).mp3 at /(1998) The Dance/03 The Other Half (Of me).mp3
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/08%20Candles.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/08 Candles.mp3 at /(1997) Enter/08 Candles.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/10%20In%20Perfect%20Harmony.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/10 In Perfect Harmony.mp3 at /(2001) Mother Earth/10 In Perfect Harmony.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/01%20Mother%20Earth.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/01 Mother Earth.mp3 at /(2001) Mother Earth/01 Mother Earth.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/03%20Frozen.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/03 Frozen.mp3 at /(2007) The Heart of Everything/03 Frozen.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/06%20Never%20Ending%20Story.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/06 Never Ending Story.mp3 at /(2001) Mother Earth/06 Never Ending Story.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/01%20Intro.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/01 Intro.mp3 at /(2004) The Silent Force/01 Intro.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/11%20Somewhere.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/11 Somewhere.mp3 at /(2004) The Silent Force/11 Somewhere.mp3
BraseroBurnURI Information retrieval for burn:///(1998)%20The%20Dance/The%20Dance.jpg
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1998) The Dance/The Dance.jpg at /(1998) The Dance/The Dance.jpg
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/06%20Grace.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/06 Grace.mp3 at /(1997) Enter/06 Grace.mp3
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter
BraseroBurnURI Adding directory (null) at /(1997) Enter/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/Enter.jpg at /(1997) Enter/Enter.jpg
BraseroBurnURI Graft already in list /(1997) Enter/03 Pearls of Light.mp3
BraseroBurnURI Graft already in list /(1997) Enter/04 Deep Within.mp3
BraseroBurnURI Graft already in list /(1997) Enter/05 Gatekeeper.mp3
BraseroBurnURI Graft already in list /(1997) Enter/06 Grace.mp3
BraseroBurnURI Graft already in list /(1997) Enter/07 Blooded.mp3
BraseroBurnURI Graft already in list /(1997) Enter/08 Candles.mp3
BraseroBurnURI Graft already in list /(1997) Enter/01 Restless.mp3
BraseroBurnURI Graft already in list /(1997) Enter/02 Enter.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/The%20Silent%20Force.jpg
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/The Silent Force.jpg at /(2004) The Silent Force/The Silent Force.jpg
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/13%20The%20Swan%20Song.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/13 The Swan Song.mp3 at /(2004) The Silent Force/13 The Swan Song.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/08%20Intro.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/08 Intro.mp3 at /(2001) Mother Earth/08 Intro.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/13%20Never%20Ending%20Story%20(Live%20at%20Lowlands).mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/13 Never Ending Story (Live at Lowlands).mp3 at /(2001) Mother Earth/13 Never Ending Story (Live at Lowlands).mp3
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/01%20Restless.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/01 Restless.mp3 at /(1997) Enter/01 Restless.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth
BraseroBurnURI Adding directory (null) at /(2001) Mother Earth/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Graft already in list /(2001) Mother Earth/06 Never Ending Story.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/11 Bittersweet.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/05 The Promise.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/03 Our Farewell.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/04 Caged.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/01 Mother Earth.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/02 Ice Queen.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/12 Mother Earth (Live at Leidse Kade).mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/13 Never Ending Story (Live at Lowlands).mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/10 In Perfect Harmony.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/07 Deceiver of Fools.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/09 Dark Wings.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/08 Intro.mp3
BraseroBurnURI Graft already in list /(2001) Mother Earth/Mother Earth.jpg
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/04%20Deep%20Within.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/04 Deep Within.mp3 at /(1997) Enter/04 Deep Within.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/05%20The%20Promise.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/05 The Promise.mp3 at /(2001) Mother Earth/05 The Promise.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/07%20Angels.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/07 Angels.mp3 at /(2004) The Silent Force/07 Angels.mp3
BraseroBurnURI Information retrieval for burn:///(1998)%20The%20Dance/02%20Another%20Day.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1998) The Dance/02 Another Day.mp3 at /(1998) The Dance/02 Another Day.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/02%20See%20Who%20I%20Am.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/02 See Who I Am.mp3 at /(2004) The Silent Force/02 See Who I Am.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/Mother%20Earth.jpg
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/Mother Earth.jpg at /(2001) Mother Earth/Mother Earth.jpg
BraseroBurnURI Information retrieval for burn:///(1997)%20Enter/03%20Pearls%20of%20Light.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(1997) Enter/03 Pearls of Light.mp3 at /(1997) Enter/03 Pearls of Light.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/11%20Bittersweet.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/11 Bittersweet.mp3 at /(2001) Mother Earth/11 Bittersweet.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/06%20Forsaken.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/06 Forsaken.mp3 at /(2004) The Silent Force/06 Forsaken.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/02%20Ice%20Queen.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/02 Ice Queen.mp3 at /(2001) Mother Earth/02 Ice Queen.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/12%20Mother%20Earth%20(Live%20at%20Leidse%20Kade).mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/12 Mother Earth (Live at Leidse Kade).mp3 at /(2001) Mother Earth/12 Mother Earth (Live at Leidse Kade).mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/03%20Jillian%20(I'd%20Give%20My%20Heart).mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/03 Jillian (I'd Give My Heart).mp3 at /(2004) The Silent Force/03 Jillian (I'd Give My Heart).mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/04%20Stand%20My%20Ground.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/04 Stand My Ground.mp3 at /(2004) The Silent Force/04 Stand My Ground.mp3
BraseroBurnURI Information retrieval for burn:///(2004)%20The%20Silent%20Force/08%20Memories.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2004) The Silent Force/08 Memories.mp3 at /(2004) The Silent Force/08 Memories.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/03%20Our%20Farewell.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/03 Our Farewell.mp3 at /(2001) Mother Earth/03 Our Farewell.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/02%20What%20Have%20You%20Done%20(feat.%20Keith%20Caputo).mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/02 What Have You Done (feat. Keith Caputo).mp3 at /(2007) The Heart of Everything/02 What Have You Done (feat. Keith Caputo).mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/04%20Our%20Solemn%20Hour.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/04 Our Solemn Hour.mp3 at /(2007) The Heart of Everything/04 Our Solemn Hour.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/05%20The%20Heart%20of%20Everything.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/05 The Heart of Everything.mp3 at /(2007) The Heart of Everything/05 The Heart of Everything.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/10%20The%20Truth%20Beneath%20The%20Rose.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/10 The Truth Beneath The Rose.mp3 at /(2007) The Heart of Everything/10 The Truth Beneath The Rose.mp3
BraseroBurnURI Information retrieval for burn:///(2001)%20Mother%20Earth/04%20Caged.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2001) Mother Earth/04 Caged.mp3 at /(2001) Mother Earth/04 Caged.mp3
BraseroBurnURI Information retrieval for burn:///(2007)%20The%20Heart%20of%20Everything/07%20The%20Cross.mp3
BraseroBurnURI Added file /home/fazl/Music/Within Temptation Discography/(2007) The Heart of Everything/07 The Cross.mp3 at /(2007) The Heart of Everything/07 The Cross.mp3
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_0H3FKV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_JJGLKV
	-exclude-list
	/tmp/brasero_tmp_0GGLKV
	-A
	Brasero-2.30.2
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stdout: 282702
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage stderr: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage Finished track successfully
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr0
	speed=10
	driveropts=burnfree
	fs=25m
	tsize=282702s
	-data
	-nopad
	-
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroWodim
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_EHEWKV
	-exclude-list
	/tmp/brasero_tmp_4EEWKV
	-A
	Brasero-2.30.2
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Assuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.10
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'RW/DVD GCC-4242N'
BraseroWodim stdout: Revision       : '0201'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1644048 = 1605 KB
BraseroWodim stdout: FIFO size      : 26214400 = 25600 KB
BraseroWodim stderr: Speed set to 1764 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   552 MB        
BraseroWodim stdout: Total size:      634 MB (62:49.38) = 282704 sectors
BraseroWodim stdout: Lout start:      634 MB (62:51/29) = 282704 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -12369 (97:17/06)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 69
BraseroWodim stdout: Manufacturer: Moser Baer India Limited
BraseroWodim stdout: Manufacturer is guessed because of the orange forum embargo.
BraseroWodim stdout: The orange forum likes to get money for recent information.
BraseroWodim stdout: The information for this media may not be correct.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 77145
BraseroWodim stdout: Starting to write CD/DVD at speed  10.0 in real TAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroGenisoimage stderr:   1.77% done, estimate finish Tue Oct 12 20:43:45 2010
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroGenisoimage stderr:   3.54% done, estimate finish Tue Oct 12 20:41:52 2010
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:   14.547s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 14.511s timeout 60s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 399 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record brasero-burn.c:2842)





####################################################################
END  END  END  END  END  END  END  END  END  END  END  END  
###################################################################
Now I've also done this in CD/DVD recorder but I don't know how to get much info from that but I have done it from K3B as well. The odd thing is that it works sometimes but most of the times it just fails. As I am writing this post now, it is actually working, but at a very slow pace. it is working at 4X when I should be able to go up to 32X. It is also unpredictable. I am writing in the DAO mode. When the K3B errors occur, it gives me an OPC failure as well and then says "probably does not like the media" which makes no sense to me.

Other info...

my Fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c4f9c06d-0e3f-4634-a586-577e12af0192 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fc125a2e-9d81-4275-9054-5459835eb363 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


###################
and my fdisk -l

Disk /dev/sda: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072b87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3730    29957120   83  Linux
/dev/sda2            3730        3896     1333249    5  Extended
/dev/sda5            3730        3896     1333248   82  Linux swap / Solaris

I've read a bunch abaout wodim and some other things but I don't see any wodim on my K3b, only growisof. But the Brasero does have the wodim in it.

Can anyone help???

---

### Post by Fazl on 2010-10-22
This is the debugging report from a failed K3B attempt

Devices
-----------------------
HL-DT-ST RW/DVD GCC-4242N 0201 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM) [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 147959 (303020032 bytes)

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-25-generic

Used versions
-----------------------
mkisofs: 1.1.10
cdrecord: 3.0

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: Cannot read drive buffer.
/usr/bin/cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 3.00 (i686-pc-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4242N'
Revision       : '0201'
Device seems to be: Generic mmc2 DVD-ROM.
Current: CD-R
Profile: DVD-ROM 
Profile: CD-ROM 
Profile: CD-R (current)
Profile: CD-RW 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1644048 = 1605 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   288 MB        
Total size:      331 MB (32:52.78) = 147959 sectors
Lout start:      332 MB (32:54/59) = 147959 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
    Capacity  Blklen/Sparesz.  Format-type  Type
      359847             2048         0x00  Formatted Media
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 211890
Starting to write CD/DVD/BD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
/usr/bin/cdrecord: Input/output error. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 12.385s timeout 200s
/usr/bin/cdrecord: OPC failed.
Writing  time:   12.421s
/usr/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=10 -sao driveropts=burnfree -data -tsize=147959s -

mkisofs
-----------------------
147959
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.35% done, estimate finish Fri Oct 22 17:53:51 2010
  0.68% done, estimate finish Fri Oct 22 17:44:23 2010
  1.02% done, estimate finish Fri Oct 22 17:41:09 2010
  1.35% done, estimate finish Fri Oct 22 17:39:31 2010

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-fazl/k3bQl7641.tmp -rational-rock -hide-list /tmp/kde-fazl/k3bWA7641.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-fazl/k3bTK7641.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-fazl/k3bdL7641.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-fazl/k3bBW7641.tmp -rational-rock -hide-list /tmp/kde-fazl/k3blL7641.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-fazl/k3bvl7641.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-fazl/k3bKh7641.tmp

---

### Post by Fazl on 2010-10-30
Does anyone have any info?? The version of CD record i am running is 

Cdrecord-ProDVD-ProBD-Clone 3.00 (i686-pc-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling

I think this info is already stated in the above texts...

---

