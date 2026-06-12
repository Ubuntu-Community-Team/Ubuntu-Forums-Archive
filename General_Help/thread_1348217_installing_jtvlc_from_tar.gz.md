---
title: "installing jtvlc from tar.gz"
date: 2009-12-07
forum: General Help
---

### Post by TheShabz on 2009-12-07
so im trying to broadcast a few videos on justin.tv and am looking to use VLC to do so. they have a wiki that says i have to use their API from here: [http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API](http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API) for it but dont offer any help in actually installing it.

my question is how do i install it from tar.gz ive downloaded it and extracted it. ./configure gives me "no such file or directory" and make gives me "make: *** No targets specified and no makefile found.  Stop."

where am i going wrong? the readme is useless

---

### Post by mc4man on 2009-12-07
You don't install it, just run in a terminal after cd'ing to the extracted folder, using ./jtvlc < whatever the commands are>

Ex of how to run, not use (won't know unless tried, would use the wiki to figure out

> doug@doug-laptop:~/Desktop/jtvlc-lin-0.41$ ./jtvlc
-----------------------------------------------------------------------
  Justin.tv Jtvlc 0.41 Help - Vladislav Yazhbin <vlad@justin.tv>
-----------------------------------------------------------------------
  Please use the following command line format:

      jtvlc login stream_key sdp_file [-d]

  For example:

      jtvlc lin_user live_gk423_c3r4 file:///home/justin/Desktop/vlc.sdp
      jtvlc mac_user live_l01d_dlj1 /Users/Justin/Desktop/vlc.sdp
      jtvlc.exe win_user live_pj42_8fkh2 c:/users/justin/vlc.sdp

  -d is an optional parameter that enables debug logging to the console

  Please see 'readme.txt' for more information.

-----------------------------------------------------------------------
  You are using the latest version.
  Jtvlc homepage:  [http://community.justin.tv/mediawiki/index.php/Vlc](http://community.justin.tv/mediawiki/index.php/Vlc)
-----------------------------------------------------------------------


---

### Post by TheShabz on 2009-12-08
yea i realized that earlier today. im still trying to get out of the .exe>gui>work mode. im trying =]

thanks though

/thread

---

