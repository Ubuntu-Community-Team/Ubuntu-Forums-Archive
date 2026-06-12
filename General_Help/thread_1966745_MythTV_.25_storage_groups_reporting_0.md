---
title: "MythTV .25 storage groups reporting 0"
date: 2012-04-27
forum: General Help
---

### Post by myth1914 on 2012-04-27
OK.  After hours of working with my Ceton card on 12.04 and not getting anywhere, I downgraded to a fresh install of 11.04 (don't ask).  I now find that I have the same issue that caused me to give up on the new distro.  I don't want to upgrade/reinstall til I get this figured out.  

I've had mythtv .25 working with all the hardware except a new 3ware 9650 raid controller.  I previously had an Intel (LSI) raid set up the same way, mounted at /var/lib/mythtv.  My storage groups all point to folders under the mount with 777 mythtv:mythtv so there should be no permission issues whatsoever.

My LiveTV gives the following output:

2012-04-27 07:54:58.820848 I  Using protocol version 72
2012-04-27 07:54:58.829927 I  Bonjour: Service registration complete: name 'Mythfrontend on Server' type '_mythfrontend._tcp.' domain: 'local.'
2012-04-27 07:55:13.706758 I  Using protocol version 72
2012-04-27 07:55:13.707514 I  Using protocol version 72
2012-04-27 07:56:36.412969 I  TV: Creating TV object
2012-04-27 07:56:36.433454 N  Resuming idle timer
2012-04-27 07:56:36.436267 N  Suspending idle timer
2012-04-27 07:56:36.439557 I  TV: Created TvPlayWindow.
2012-04-27 07:56:36.459007 I  TV: Attempting to change from None to WatchingLiveTV
2012-04-27 07:56:36.459037 I  MythCoreContext: Connecting to backend server: 192.168.2.108:6543 (try 1 of 1)
2012-04-27 07:56:36.459419 I  Using protocol version 72
2012-04-27 07:56:36.460609 N  TV: Spawning LiveTV Recorder -- begin
2012-04-27 07:56:36.607916 N  TV: Spawning LiveTV Recorder -- end
2012-04-27 07:56:36.608453 E  GetEntryAt(-1) failed.
2012-04-27 07:56:36.608466 E  It appears that your backend may be misconfigured.  Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors.  This issue is commonly caused by failing to complete all setup steps properly.  You may wish to review the documentation for mythtv-setup.
2012-04-27 07:56:36.608560 E  EntryToProgram(0@Wed Dec 31 17:00:00 1969) failed to get pginfo
2012-04-27 07:56:36.608578 E  TV: HandleStateChange(): LiveTV not successfully started
2012-04-27 07:56:36.608676 E  TV: LiveTV not successfully started
2012-04-27 07:56:36.612757 I  TV: Main UI disabled.
2012-04-27 07:56:36.612987 I  TV: Entering main playback loop.
2012-04-27 07:56:36.613319 I  ScreenSaverX11Private: DPMS Deactivated 1
2012-04-27 07:56:36.613434 I  TV: Exiting main playback loop.
2012-04-27 07:56:36.624720 N  Resuming idle timer
2012-04-27 07:57:03.753313 N  Resuming idle timer
2012-04-27 07:57:03.754895 N  Resuming idle timer
2012-04-27 07:57:03.756375 I  Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on Server'
2012-04-27 07:57:03.756556 I  RAOP Device: Cleaning up.
2012-04-27 07:57:03.756579 I  Bonjour: De-registering service '_raop._tcp.' on '5757464f6046@MythTV on Server'
2012-04-27 07:57:03.756840 I  AirPay: Cleaning up.
2012-04-27 07:57:03.756863 I  Deleting UPnP client...
2012-04-27 07:57:04.682998 I  Waiting for threads to exit.
2012-04-27 07:57:06.362957 I  ScreenSaverX11Private: DPMS Reactivated 1

and my backend log:

Apr 27 07:56:36 Server mythbackend[1681]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
Apr 27 07:56:36 Server mythbackend[1681]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Apr 27 07:56:36 Server mythbackend[1681]: E CoreContext autoexpire.cpp:161 (CalcParams) AutoExpire: Filesystem Info cache is empty, unable to calculate necessary parameters.
Apr 27 07:56:36 Server mythbackend[1681]: E TVRecEvent ThreadedFileWriter.cpp:119 (Open) TFW(/var/lib/mythtv/livetv/1010_20120427075636.mpg:-1): Opening file '/var/lib/mythtv/livetv/1010_20120427075636.mpg'.#012#011#011#011eno: Permission denied (13)
Apr 27 07:56:36 Server mythbackend[1681]: E TVRecEvent tv_rec.cpp:4348 (GetProgramRingBufferForLiveTV) TVRec(1): RingBuffer '/var/lib/mythtv/livetv/1010_20120427075636.mpg' not open...
Apr 27 07:56:36 Server mythbackend[1681]: E TVRecEvent tv_rec.cpp:4384 (CreateLiveTVRingBuffer) TVRec(1): CreateLiveTVRingBuffer(10) failed
Apr 27 07:56:36 Server mythbackend[1681]: E TVRecEvent tv_rec.cpp:3684 (TuningFrequency) TVRec(1): Failed to create RingBuffer 1
Apr 27 07:56:36 Server mythbackend[1681]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None


Before anyone still points to permissions, this is the interesting part:

df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             902G  4.1G  852G   1% /
none                  7.8G  760K  7.8G   1% /dev
none                  7.9G  112K  7.9G   1% /dev/shm
none                  7.9G  388K  7.9G   1% /var/run
none                  7.9G     0  7.9G   0% /var/lock
/dev/sdb1             3.7T  2.1T  1.7T  56% /var/lib/mythtv

Yet mythweb:

Disk Usage Summary:
      
[LIST]
[*]Total Disk Space:
[LIST]
[*]Total Space: 0 MB
[*]Space Used: 0 MB
[*]Space Free: 0 MB
[/LIST]
[/LIST]
Any thoughts/ideas?

---

### Post by myth1914 on 2012-04-27
D*** it!

OK, so minutes later, I figured this out...  the parent, being /var/lib/mythtv was owned by me with 700.  once I updated that, all is well.  So.... hopefully that helps someone down the road.  Now on to another reinstall and hoping I can get it up on 12.04

---

