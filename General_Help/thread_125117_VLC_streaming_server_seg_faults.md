---
title: "VLC streaming server seg faults"
date: 2006-02-03
forum: General Help
---

### Post by bvucinic on 2006-02-03
The VLC streaming server crashes (segmentation fault) when I want to see a video from my ubuntu 5.10 PC on my TV connected via a set-top-box.
My ADSL provider is French 9telecom (neuf) who provided the set-top-box and the configuration script for the videolan server (mp9.cfg run by MP9.sh).

This is the end of the log:

[00000277] http interface debug: 716: value = "#transcode{vcodec=mp2v,vb=3072,scale=1,acodec=mpga,ab=128,channels=2}:duplicate{dst=std{access=udp,mux=ts,url=192.168.1.199:26134}}"
[00000277] http interface debug: requested playlist pause
[00000277] http interface debug: 716: value = "#transcode{vcodec=mp2v,vb=3072,scale=1,acodec=mpga,ab=128,channels=2}:duplicate{dst=std{access=udp,mux=ts,url=192.168.1.199:26134}}"
[00000271] main playlist debug: nothing requested, starting
[00000271] main playlist debug: creating new input thread
[00000281] main input debug: waiting for thread completion
[00000281] main input debug: thread 3027340208 (input) created at priority 0 (src/input/input.c:230)
[00000282] main stream output debug: stream=`transcode'
[00000283] main private debug: looking for sout stream module: 1 candidate
[00000277] http interface debug: requested playlist play
[00000277] http interface debug: 716: value = "#transcode{vcodec=mp2v,vb=3072,scale=1,acodec=mpga,ab=128,channels=2}:duplicate{dst=std{access=udp,mux=ts,url=192.168.1.199:26134}}"
[00000282] main stream output debug: stream=`duplicate'
[00000286] main private debug: looking for sout stream module: 1 candidate
[00000286] stream_out_duplicate private debug: creating 'duplicate'
[00000286] stream_out_duplicate private debug:  * adding `std{access=udp,mux=ts,url=192.168.1.199:26134}'
[00000282] main stream output debug: stream=`std'
[00000288] main private debug: looking for sout stream module: 1 candidate
[00000288] main private debug: set sout option: sout-standard-access to udp
[00000288] main private debug: set sout option: sout-standard-mux to ts
[00000288] main private debug: set sout option: sout-standard-url to 192.168.1.199:26134
[00000288] stream_out_standard private debug: creating `udp/ts://192.168.1.199:26134'
[00000288] stream_out_standard private debug: extention is 199:26134
[00000288] stream_out_standard private debug: extention -> mux=(null)
[00000288] stream_out_standard private debug: using `udp/ts://192.168.1.199:26134'
[00000290] main private debug: looking for sout access module: 1 candidate
[00000292] main private debug: looking for network module: 1 candidate
[00000186] main module debug: using network module "ipv4"
[00000186] main module debug: unlocking module "ipv4"
[00000292] main private debug: thread 3018898352 (sout write thread) created at priority 0 (udp.c:295)
[00000290] access_output_udp private debug: udp access output opened(192.168.1.199:26134)
[00000243] main module debug: using sout access module "access_output_udp"
[00000288] stream_out_standard private debug: access opened
[00000294] main private debug: looking for sout mux module: 1 candidate
/usr/share/vlc/MP9.sh: line 3:   657 Segmentation fault      vlc -vvv -I http --http-host 192.168.1.2:26180 --language en --config mp9.cfg --verbose 2
:confused: 

Any help would be highly appreciated.
Thanks in advance, Bojan

P.S. by the way the VLC client runs just fine! (I can watch videos stored on the disk)

---

