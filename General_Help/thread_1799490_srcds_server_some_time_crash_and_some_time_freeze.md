---
title: "srcds server some time crash and some time freeze"
date: 2011-07-07
forum: General Help
---

### Post by thxyou on 2011-07-07
BASIC INFO

Server OS: ubuntu Release 11.04 (natty) 32-bit kernel linux 2.6.38-8generic GNOME 2.32.1

Processor: intel(R) Xeon(R) CPU X3210 @ 2.13GHZ

Ram: 2GB

Game(s):Counter Strike Source

Start Up Command: ./srcds_run -console -game cstrike +map awp_lego +maxplayers 24 -port 27015 

Admin Mods: SourceMod 1.3.8   MetaMod 1.8.7

INSTALLING INFO
I dont know

NETWORK AND BANDWIDTH INFO
i dont know 

CONFIG ISSUES
```

// server name
hostname "my name server"

// rcon passsword
rcon_password  // rcon disabled

//download
sv_downloadurl "http://myipserver/orangebox/cstrike/"
sv_allowdownload 1
sv_allowupload 1



// Advanced RCON
sv_rcon_banpenalty 60
sv_rcon_maxfailures 3
sv_rcon_minfailures 3
sv_rcon_minfailuretime 30

// server cvars
sv_use_steam_voice 0
mp_friendlyfire 0
mp_footsteps 1
mp_autoteambalance 1
mp_autokick 0
mp_flashlight 1
mp_tkpunish 1
mp_forcecamera 0
sv_alltalk 1
sv_pausable 0
sv_cheats 0
sv_consistency 1
sv_allowupload 1
sv_allowdownload 1
sv_maxspeed 320
mp_limitteams 2
mp_hostagepenalty 5
sv_voiceenable 1
mp_allowspectators 1
mp_timelimit 10
mp_chattime 10
sv_timeout 65

// round specific cvars
mp_freezetime 0
mp_roundtime 3
mp_startmoney 800
mp_c4timer 45
mp_fraglimit 0
mp_maxrounds 0
mp_winlimit 0
mp_playerid 0
mp_spawnprotectiontime 5
mp_tkpunish 0

// bandwidth rates/settings
sv_minrate 30000
sv_maxrate 30000
decalfrequency 10
sv_maxupdaterate 66
sv_minupdaterate 66
sv_mincmdrate 66
sv_maxcmdrate 66

// server logging
log off
sv_logbans 0
sv_logecho 1
sv_logfile 1
sv_log_onefile 0

// operation
sv_lan 0
sv_region 3
sv_contact algeriacss@msn.com

// anti cheat
sv_max_usercmd_future_ticks 2
sv_consistency 1
sv_allow_wait_command 0
sv_pure 0

// execute ban files
exec banned_user.cfg
exec banned_ip.cfg 
writeip
```ADMIN MOD ISSUES
i dont know

READ ME LINK
i dont know

when  is crach i see this in my consol
```
*** glibc detected *** ./srcds_linux: free(): invalid pointer: 0x0ad8b048 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6b961)[0xa8a961]
/lib/i386-linux-gnu/libc.so.6(+0x6d28b)[0xa8c28b]
/lib/i386-linux-gnu/libc.so.6(cfree+0x6d)[0xa8f41d]
bin/libtier0.so(_ZdlPv+0x22)[0xcefa02]
bin/steamclient.so(_ZN10GameServer5Users12CUserManager17UseUnknownSteamIDEj+0x45)[0x87fb5b]
bin/steamclient.so(_ZN10GameServer5Users5CUser14LoadTicketTypeEPKvj+0x1fb)[0x880b81]
bin/steamclient.so(_ZN10GameServer5Users5CUserC1EPKvjjPN5Other10ISteamUserENS0_19ESteamTicketVer&#8203;sionE+0x5c)[0x8813c2]
bin/steamclient.so(_ZN8Adapters19CSteamGameServer01016BeginAuthSessionEPKvi8CSteamID+0x38)[0x86f66c]
/root/srcds_l/orangebox/bin/engine.so(+0x1bcfa0)[0x5a3afa0]
/root/srcds_l/orangebox/bin/engine.so(+0x8f95f)[0x590d95f]
/root/srcds_l/orangebox/bin/engine.so(+0x901d0)[0x590e1d0]
/root/srcds_l/orangebox/bin/engine.so(+0x9185e)[0x590f85e]
/root/srcds_l/orangebox/bin/engine.so(+0x1575a1)[0x59d55a1]
/root/srcds_l/orangebox/bin/engine.so(+0x93e35)[0x5911e35]
/root/srcds_l/orangebox/bin/engine.so(+0x1a70fd)[0x5a250fd]
/root/srcds_l/orangebox/bin/engine.so(+0x10a167)[0x5988167]
/root/srcds_l/orangebox/bin/engine.so(+0x10ad94)[0x5988d94]
/root/srcds_l/orangebox/bin/engine.so(+0x114295)[0x5992295]
/root/srcds_l/orangebox/bin/engine.so(+0x114ac1)[0x5992ac1]
/root/srcds_l/orangebox/bin/engine.so(+0x114cc8)[0x5992cc8]
/root/srcds_l/orangebox/bin/engine.so(+0x1c7df4)[0x5a45df4]
/root/srcds_l/orangebox/bin/engine.so(+0x1c4639)[0x5a42639]
bin/dedicated.so(+0x4da20)[0x493a20]
bin/dedicated.so(+0x4d777)[0x493777]
/root/srcds_l/orangebox/bin/engine.so(+0x1c4c5b)[0x5a42c5b]
/root/srcds_l/orangebox/bin/engine.so(+0x1dd9a1)[0x5a5b9a1]
/root/srcds_l/orangebox/bin/engine.so(+0x1c5c0a)[0x5a43c0a]
bin/dedicated.so(+0x4dc23)[0x493c23]
bin/dedicated.so(+0x51471)[0x497471]
bin/dedicated.so(+0x52ced)[0x498ced]
bin/dedicated.so(+0x51471)[0x497471]
bin/dedicated.so(+0x4e03a)[0x49403a]
bin/dedicated.so(DedicatedMain+0x24)[0x49532f]
./srcds_linux[0x80488ec]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0xa35e37]
./srcds_linux[0x8048771]
======= Memory map: ========
00110000-00111000 rwxp 00000000 00:00 0
00111000-0011b000 r-xp 00000000 08:02 3416108    /lib/i386-linux-gnu/libnss_files-2.13.so
0011b000-0011c000 r-xp 00009000 08:02 3416108    /lib/i386-linux-gnu/libnss_files-2.13.so
0011c000-0011d000 rwxp 0000a000 08:02 3416108    /lib/i386-linux-gnu/libnss_files-2.13.so
0011e000-0011f000 rwxp 00000000 00:00 0
0011f000-00133000 r-xp 00000000 08:02 12525574   /root/srcds_l/orangebox/bin/libsteam_api.so
00133000-00134000 rwxp 00014000 08:02 12525574   /root/srcds_l/orangebox/bin/libsteam_api.so
00134000-0013a000 rwxp 00000000 00:00 0
0013a000-0014f000 r-xp 00000000 08:02 12525583   /root/srcds_l/orangebox/bin/shaderapiempty.so
0014f000-00151000 r-xp 00014000 08:02 12525583   /root/srcds_l/orangebox/bin/shaderapiempty.so
00151000-00152000 rwxp 00016000 08:02 12525583   /root/srcds_l/orangebox/bin/shaderapiempty.so
00152000-00153000 r-xp 00000000 08:02 4227334    /root/srcds_l/orangebox/cstrike/addons/sourcemod/bin/sourcemod_mm_i486.so
00153000-00154000 rwxp 00001000 08:02 4227334    /root/srcds_l/orangebox/cstrike/addons/sourcemod/bin/sourcemod_mm_i486.so
00154000-00156000 r-xp 00000000 08:02 3417559    /lib/libnss_mdns4_minimal.so.2
00156000-00157000 r-xp 00001000 08:02 3417559    /lib/libnss_mdns4_minimal.so.2
00157000-00158000 rwxp 00002000 08:02 3417559    /lib/libnss_mdns4_minimal.so.2
00158000-00159000 r-xp 00000000 00:00 0          [vdso]
00159000-00184000 rwxp 00000000 00:00 0
00184000-001b6000 r-xp 00000000 08:02 12525584   /root/srcds_l/orangebox/bin/soundemittersystem.so
001b6000-001b7000 ---p 00032000 08:02 12525584   /root/srcds_l/orangebox/bin/soundemittersystem.so
001b7000-001b8000 r-xp 00032000 08:02 12525584   /root/srcds_l/orangebox/bin/soundemittersystem.so
001b8000-001b9000 rwxp 00033000 08:02 12525584   /root/srcds_l/orangebox/bin/soundemittersystem.so
001b9000-001bb000 rwxp 00000000 00:00 0
001bb000-001c1000 r-xp 00000000 08:02 4235727    /root/srcds_l/orangebox/cstrike/addons/sourcemod/extensions/updater.ext.so
001c1000-001c2000 rwxp 00005000 08:02 4235727    /root/srcds_l/orangebox/cstrike/addons/sourcemod/extensions/updater.ext.so
001c2000-001c9000 r-xp 00000000 08:02 3416085    /lib/i386-linux-gnu/librt-2.13.so
001c9000-001ca000 r-xp 00006000 08:02 3416085    /lib/i386-linux-gnu/librt-2.13.so
001ca000-001cb000 rwxp 00007000 08:02 3416085    /lib/i386-linux-gnu/librt-2.13.so
001ce000-00209000 rwxp 00000000 00:00 0
00209000-0020d000 r-xp 00000000 08:02 4235732    /root/srcds_l/orangebox/cstrike/addons/sourcemod/extensions/game.cstrike.ext.2.ep2v.so
0020d000-0020e000 rwxp 00003000 08:02 4235732    /root/srcds_l/orangebox/cstrike/addons/sourcemod/extensions/game.cstrike.ext.2.ep2v.so
0020e000-00214000 r-xp 00000000 08:02 4235731    /root/srcds_l/orangebox/cstrike/addons/sourcemod/extensions/bintools.ext.2.ep2v.so
00214000-00215000 rwxp 00005000 08:02 4235731    /root/srcds_l/orangebox/cstrike/addons/sourcemod/extensions/bintools.ext.2.ep2v.so
00217000-0023b000 r-xp 00000000 08:02 3416105    /lib/i386-linux-gnu/libm-2.13.so
0023b000-0023c000 r-xp 00023000 08:02 3416105    /lib/i386-linux-gnu/libm-2.13.so
0023c000-0023d000 rwxp 00024000 08:02 3416105    /lib/i386-linux-gnu/libm-2.13.so
0023d000-00253000 r-xp 00000000 08:02 12525582   /root/srcds_l/orangebox/bin/scenefilecache.so
00253000-00254000 r-xp 00015000 08:02 12525582   /root/srcds_l/orangebox/bin/scenefilecache.so
00254000-00255000 rwxp 00016000 08:02 12525582   /root/srcds_l/orangebox/bin/scenefilecache.so
00255000-00256000 rwxp 00000000 00:00 0
00256000-0025a000 r-xp 00000000 08:02 3416091    /lib/i386-linux-gnu/libnss_dns-2.13.so
0025a000-0025b000 r-xp 00004000 08:02 3416091    /lib/i386-linux-gnu/libnss_dns-2.13.so
0025b000-0025c000 rwxp 00005000 08:02 3416091    /lib/i386-linux-gnu/libnss_dns-2.13.so
0025d000-0028f000 r-xp 00000000 08:02 12525578   /root/srcds_l/orangebox/bin/libvstdlib.so
0028f000-00290000 ---p 00032000 08:02 12525578   /root/srcds_l/orangebox/bin/libvstdlib.so
00290000-00292000 rwxp 00032000 08:02 12525578   /root/srcds_l/orangebox/bin/libvstdlib.so
00292000-0030d000 rwxp 00000000 00:00 0
0030d000-0030e000 ---p 00000000 00:00 0
0030e000-0040e000 rwxp 00000000 00:00 0
0040e000-00428000 r-xp 00000000 08:02 3416132    /lib/i386-linux-gnu/libgcc_s.so.1
00428000-00429000 r-xp 00019000 08:02 3416132    /lib/i386-linux-gnu/libgcc_s.so.1
00429000-0042a000 rwxp 0001a000 08:02 3416132    /lib/i386-linux-gnu/libgcc_s.so.1Aborted
Add "-debug" to the ./srcds_run command line to generate a debug.log to help with solving this problem
Wed Jul  6 20:24:05 CEST 2011: Server restart in 10 seconds
Running a benchmark to measure system clock frequency...
Finished RDTSC test. To prevent the startup delay from this benchmark, set the environment variable RDTSC_FREQUENCY to 2133.000000 on this system. This value is dependent upon the CPU clock speed and architecture and should be determined separately for each server. The use of this mechanism for timing can be disabled by setting RDTSC_FREQUENCY to 'disabled'.
Using breakpad minidump system
Using breakpad crash handler

Console initialized. etc
```when is freeze  the server is of line and idont see any error in consol  and i cant type in consol and i must close it and open server.sh to run it again 

and this my syslog  
var/log/syslog
```
Jul  7 07:36:39 leaseweb rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="751" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul  7 07:36:39 leaseweb anacron[7121]: Job `cron.daily' terminated
Jul  7 07:36:39 leaseweb anacron[7121]: Normal exit (1 job run)
Jul  7 07:39:01 leaseweb CRON[7346]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 08:09:01 leaseweb CRON[7363]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 08:17:01 leaseweb CRON[7372]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 08:39:01 leaseweb CRON[7385]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 09:09:01 leaseweb CRON[7403]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 09:17:01 leaseweb CRON[7413]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 09:39:01 leaseweb CRON[7431]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 10:09:01 leaseweb CRON[8672]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 10:17:01 leaseweb CRON[8681]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 10:39:01 leaseweb CRON[8692]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 11:09:01 leaseweb CRON[8708]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 11:17:01 leaseweb CRON[8717]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 11:39:01 leaseweb CRON[8728]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 12:09:01 leaseweb CRON[8745]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 12:17:01 leaseweb CRON[8754]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 12:39:01 leaseweb CRON[8765]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 13:09:01 leaseweb CRON[8797]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 13:17:01 leaseweb CRON[8807]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 13:39:01 leaseweb CRON[8818]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 14:09:01 leaseweb CRON[8834]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 14:17:01 leaseweb CRON[8843]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 14:39:01 leaseweb CRON[8854]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 15:09:01 leaseweb CRON[8872]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 15:17:01 leaseweb CRON[8881]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 15:39:01 leaseweb CRON[8892]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 16:09:01 leaseweb CRON[8910]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 16:17:01 leaseweb CRON[8919]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 16:39:01 leaseweb CRON[8930]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 17:09:01 leaseweb CRON[8948]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 17:17:01 leaseweb CRON[8957]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 17:39:01 leaseweb CRON[8968]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 18:03:45 leaseweb kernel: [164608.478777] UDP: short packet: From 95.90.115.53:1024 1024/105 to 95.211.1.10:0
Jul  7 18:09:01 leaseweb CRON[8986]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  7 18:17:01 leaseweb CRON[9002]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 18:39:01 leaseweb CRON[9076]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)

```so what i can do ?

---

