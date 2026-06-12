---
title: "computer complete freeze"
date: 2009-12-17
forum: General Help
---

### Post by meep_meep on 2009-12-17
Hi all,

Thanks for any help in advance!

I recently built my first computer

AMD Phenom II x4 955
4 Gb Corsair 1333MHz, DDR3
MSI motherboard 770-c45
Gigabyte 9600GT silent cell
500w artic cooling
d-link dwl g510 wifi card

In Ubuntu 9.10 x64 Fresh install with all the updates, it crashes when playing flash (iplayer) full screen.  The whole computer freezes and the sound jutters, replaying the same 1 second sound.  I have to hold down restart to it.  I have no other program open at the time, only firefox and flash.  Nothing responds, so I cant kill X or press control, alt F2.

The install is fairly standard but I switched autospawn for pulseaudio off so I could kill it to play counterstrike source.  Will this causes the freezes in flash?

Also in windows if i have Chrome and spotify open at the same time after about 20 mins the whole computer will freeze the same way with the sound juttering, replaying the same small sound piece.

What kind of problem is this?  Are they linked?  I was thinking that I might have a problem with my RAM but my motherboard recognises them properly in the BIOS.  I also went in and changed it to the correct timings for my RAM.

I've also been trying to install a cyberlink remote with LIRC which I think has been crashing Banshee.  I don't know whether this affects pulseaudio or the kernel.

Both times before I've had a crash recently I've had one of these messages

pulseaudio[2048]: ratelimit.c: X events suppressed

and recently before an iPlayer Full Screen Crash it came up with this in the Kernel Log under messages

kernel: [ 1076.558378] npviewer.bin[3131]: segfault at ff999ed8 ip 00000000ff999ed8 sp 00000000ffb78d8c error 14


any ideas?  thanks for your time and help

meep

---

### Post by meep_meep on 2009-12-17
This is what was outputted before my last full screen iplayer flash freeze up/ crash.  The computer automatically restarted....

```
Dec 17 18:38:10 meep pulseaudio[2048]: ratelimit.c: 112 events suppressed
Dec 17 18:41:41 meep rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="911" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 17 18:51:40 meep kernel: [ 1076.558378] npviewer.bin[3131]: segfault at ff999ed8 ip 00000000ff999ed8 sp 00000000ffb78d8c error 14
Dec 17 18:51:52 meep pulseaudio[2048]: ratelimit.c: 156 events suppressed
Dec 17 18:52:00 meep pulseaudio[2048]: ratelimit.c: 168 events suppressed
Dec 17 19:29:09 meep kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 17 19:29:09 meep rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="798" x-info="http://www.rsyslog.com"] (re)start
Dec 17 19:29:09 meep rsyslogd: rsyslogd's groupid changed to 102
Dec 17 19:29:09 meep rsyslogd: rsyslogd's userid changed to 101
```

---

### Post by davec64 on 2009-12-17
Unfortunately this is a known issue.

If you google CPU at 100% and flash you'll see the threads. There are a lot of suggested work arounds but for me turning off Desktop affects allowed me to watch flash video's in web pages.

Possibly worth a try! :)

Also have a look here:
[http://ubuntuforums.org/showthread.php?t=1146943]("http://ubuntuforums.org/showthread.php?t=1146943")

Might help also!

---

### Post by meep_meep on 2009-12-17
I just had another crash in full screen flash with iplayer but in the logs there are no references to a npviewer segfault and just this...

```
ec 17 22:39:15 meep pulseaudio[1980]: ratelimit.c: 117 events suppressed
```

so maybe its pulseaudio crashing all this time..

so i removed pulseaudio according to this guide [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)

---

### Post by meep_meep on 2009-12-21
I'm now running just ALSA audio with no pulseaudio and I used sudo metacity --replace so that compiz would not run.  My system still crashed. So I found a bug report where people at first thought it was pulseaudio or compiz or flash but turns out it could be the nvidia driver so i might change it to the open source one.  Any how now im running vista all day with ubuntu in a virtualbox..... kind of disappointing to say the least!

---

### Post by llawwehttam on 2009-12-28
Sorry I'm a bit late. The 32 bit flash plugin is awful in 64 bit. Adobe has released the only 64-bit version of Flash Player 10 for Linux! It currently isn't in the repositories because it's still in alpha, but it's so much more stable than even the final 32-bit version. To install it, download the .tar.gz file at the bottom of this page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Next, extract the file to your home folder; then just enter this into a terminal window:

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

It worked for me so hope it will help you.

---

