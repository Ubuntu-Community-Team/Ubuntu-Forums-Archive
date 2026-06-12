---
title: "FROSTWIRE error/problem"
date: 2010-01-15
forum: General Help
---

### Post by JfaSho on 2010-01-15
Getting an ODD frostwire problem.. it wont play sound, and it continues to scroll through my playlist doing nothing. This is the error i got.

FrostWire version 4.18.6
Java version 1.6.0_15 from Sun Microsystems Inc.
Linux v. 2.6.31-17-generic-pae on i386
Free/total memory: 5034552/66650112

java.lang.AssertionError
	at com.limegroup.gnutella.gui.mp3.LimeWirePlayer.loading(Unknown Source)
	at com.limegroup.gnutella.gui.mp3.LimeWirePlayer.playing(Unknown Source)
	at com.limegroup.gnutella.gui.mp3.LimeWirePlayer.playSong(Unknown Source)
	at com.limegroup.gnutella.gui.mp3.MediaPlayerComponent$SongLoader.run(Unknown Source)
	at org.limewire.concurrent.ThreadPoolExecutor.runWorker(Unknown Source)
	at org.limewire.concurrent.ThreadPoolExecutor$Worker.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:619)


Detail: Uncaught thread error: SongProcessor
CLASSPATH:
  /usr/lib/frostwire/FrostWire.jar


-- listing session information --
Current thread: SongProcessor
Active Threads: 21
Uptime: 10:06
Is Connected: true
Number of Ultrapeer -> Ultrapeer Connections: 0
Number of Ultrapeer -> Leaf Connections: 0
Number of Leaf -> Ultrapeer Connections: 5
Number of Old Connections: 0
Acting as Ultrapeer: false
Acting as Shielded Leaf: true
Number of Active Uploads: 0
Number of Queued Uploads: 0
Number of Active Managed Downloads: 0
Number of Active HTTP Downloaders: 0
Number of Waiting Downloads: 1
Received incoming this session: true
Number of Shared Files: 931
Guess Capable: true
Received Solicited UDP: true
SIMPP version: 3
Port Stable: true
FWT Capable: true
Last Reported Port: 6346
External Port: 40506
IP Pongs Received: 0
Number of Content Response URNs: 0
Number of CreationTimeCache URNs: 922
VF Byte Cache Size: 0
VF Verify Cache Size: 0
VF Queue Size: 0
ByteBuffer Cache Size: 5482
Number of Waiting Sockets: 0
Number of Pending Timeouts: 0
Peak Number of Thread: 35
Number of SP2 Workarounds: 0
System Load Avg: -1.0
Objects Pending GC: 0
Free Space In Settings: 91197251584
Free Space In Incomplete: 91197251584
Free Space In Downloads: 91197251584
Heap Memory Usage: init = 0(0K) used = 61615560(60171K) committed = 66650112(65088K) max = 66650112(65088K)
Non-Heap Memory Usage: init = 33718272(32928K) used = 41246896(40280K) committed = 48758784(47616K) max = 121634816(118784K)
SlotManager dump:: active:0:0 1:0 2:0 queued:0:0 1:0 2:0 resumable:0:0 1:0 2:0 bw now:0.0 session avg:0.0
Number of select calls: 3471
Number of immediate selects: 71
Average time in select: 174021036

-- listing threads --
Timer-2: 1
JmDNS.RecordReaper: 1
Timer-0: 1
AWT-Shutdown: 1
Timer-1: 1
JmDNS.SocketListener: 1
QRPPropagator: 1
Deadlock Detection Thread: 1
AWT-XAWT: 1
User event dispatch thread: 1
QueryUnicaster: 1
ContentProcessor: 1
LimewirePlayer: 1
AWT-EventQueue-0: 1
Thread-7: 1
Java Sound Event Dispatcher: 1
SongProcessor: 1
MulticastService: 1
NIODispatcher: 1
DestroyJavaVM: 1
Message-Executor: 1


-- listing properties --
WINDOW_Y=117
FORCE_IP_ADDRESS=true
LAST_HTTP_FAILOVER=1263573167409
WINDOW_X=337
TOTAL_CONNECTION_TIME=235672
UPNP_IN_USE=true
INSTALLED=true
UI_LIBRARY_TREE_DIVIDER_LOCATION=130
AVERAGE_UPTIME=238
TOTAL_UPTIME=477
MAX_UPLOAD_BYTES_PER_SEC=3
INTRO_LOCAL_LINK=http://www.frostclick.com/wp/index.ph...
COUNTRY=
LAST_SHUTDOWN_TIME=1263569675751
APP_WIDTH=1271
SESSIONS=2
CHAT_IRC_NICK=
FORCED_PORT=40506
FRACTIONAL_UPTIME=4.1533564E-4
LAST_EXPIRE_TIME=1263572614762
TOTAL_CONNECTIONS=1
MAX_DOWNLOAD_BYTES_PER_SEC=7
AFTER_SEARCH_LOCAL_LINK=http://www.frostclick.com/wp/index.ph...
LAST_UPDATE_TIMESTAMP=1
RUN_ONCE=true
INTRO_URL=file:///home/jriehle87/.frostwire4.18...
APP_HEIGHT=790
INTRO_TORRENT_LINK=http://www.frostclick.com/torrents/au...
MAX_SIM_DOWNLOAD=8
INTRO_NETWORK_LINK=http://www.frostclick.com/wp/index.ph...
AFTER_SEARCH_TORRENT_LINK=http://www.frostclick.com/torrents/vi...
EVER_ACCEPTED_INCOMING=true
CLIENT_ID=508C0A8B450C4E9A3E981FC6FA5AD000
AFTER_SEARCH_NETWORK_LINK=http://www.frostclick.com/wp/index.ph...
AFTER_SEARCH_URL=file:///home/jriehle87/.frostwire4.18...
CHAT_SERVER=chat.frostwire.com


**************** Comments from the user ****************
Please add any comments you may have (e.g what caused the error).
Thank you and please use English.

---

