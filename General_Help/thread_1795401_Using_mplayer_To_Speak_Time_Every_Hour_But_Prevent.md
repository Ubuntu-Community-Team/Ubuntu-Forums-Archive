---
title: "Using mplayer To Speak Time Every Hour But Prevent Sending of Mail"
date: 2011-07-02
forum: General Help
---

### Post by GraysonPeddie on 2011-07-02
[SIZE="3"][FONT="Lucida Sans Unicode"]How do I prevent mplayer from sending e-mail by the time mplayer plays the wave file that speaks the time?[/FONT][/SIZE]

Here is the script I use to speak time. I use my natural voice to record like this:

```
"the time is ... 1 ... 2 ... 3 ... 4 ... 5 ... 6 ... 7 ... 8 ... 9 ... 10 ... 11 ... 12 ... A M  ... P M
```

Once done, I separate every parts of the waveform (separated by "...") and have it as thetimeis.wav, 01.wav, 02.wav, 03.wav, etc.

Last, but not least, I wrote the script:

```
#!/bin/bash
# Say time
PATH=/fileserver/soundfiles/speakclock
SOX=/usr/bin/sox
DATE=/bin/date
$SOX $PATH/thetimeis.wav $PATH/$($DATE '+%I').wav $PATH/$($DATE '+%p').wav $PATH/tmp.wav
/usr/bin/mplayer -ao alsa $PATH/tmp.wav > /dev/null
/bin/rm $PATH/tmp.wav
#/bin/cat /dev/null > /var/mail/grayson
exit 0
```

Note that I've commented out /bin/cat as a bandage solution to delete mail after mplayer plays the file. I said "bandage solution" because if I have grayson@ubuntu-server forward mail to my e-mail account through SMTP relay, I'm going to be seeing the e-mail messages sent every hour and I need to stop this from happening in the first place.

Example of the mail I've been getting in /var/mail/grayson:

```
From grayson@ubuntu-server  Sat Jul  2 14:00:05 2011
Return-Path: <grayson@ubuntu-server>
X-Original-To: grayson
Delivered-To: grayson@ubuntu-server
Received: by ubuntu-server (Postfix, from userid 1000)
        id 88FFC5F7B4; Sat,  2 Jul 2011 14:00:05 -0400 (EDT)
From: root@ubuntu-server (Cron Daemon)
To: grayson@ubuntu-server
Subject: Cron <grayson@ubuntu-server> /fileserver/shell_scripts/saytime_hour
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/grayson>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=grayson>
Message-Id: <20110702180005.88FFC5F7B4@ubuntu-server>
Date: Sat,  2 Jul 2011 14:00:01 -0400 (EDT)

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing /fileserver/soundfiles/speakclock/tmp.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 1.0 (01.0) ??,?%
A:   0.0 (00.0) of 1.0 (01.0)  0.0%
A:   0.4 (00.3) of 1.0 (01.0)  0.0%
A:   0.4 (00.3) of 1.0 (01.0)  0.0%
A:   0.4 (00.4) of 1.0 (01.0)  0.0%
A:   0.4 (00.4) of 1.0 (01.0)  0.0%
A:   0.5 (00.4) of 1.0 (01.0)  0.0%
A:   0.5 (00.5) of 1.0 (01.0)  0.0%
A:   0.5 (00.5) of 1.0 (01.0)  0.0%
A:   0.6 (00.5) of 1.0 (01.0)  0.0%
A:   0.6 (00.5) of 1.0 (01.0)  0.0%
A:   0.6 (00.6) of 1.0 (01.0)  0.0%
A:   0.7 (00.6) of 1.0 (01.0)  0.0%
A:   0.7 (00.6) of 1.0 (01.0)  0.0%
A:   0.7 (00.6) of 1.0 (01.0)  0.0%
A:   0.7 (00.7) of 1.0 (01.0)  0.0%
A:   0.8 (00.7) of 1.0 (01.0)  0.0%
A:   0.8 (00.7) of 1.0 (01.0)  0.0%
A:   0.8 (00.8) of 1.0 (01.0)  0.0%
A:   0.9 (00.8) of 1.0 (01.0)  0.0%
A:   0.9 (00.8) of 1.0 (01.0)  0.0%
A:   0.9 (00.9) of 1.0 (01.0)  0.0%
A:   0.9 (00.9) of 1.0 (01.0)  0.0%
A:   1.0 (00.9) of 1.0 (01.0)  0.0%
A:   1.0 (01.0) of 1.0 (01.0)  0.0%
A:   1.0 (01.0) of 1.0 (01.0)  0.0%
A:   1.1 (01.0) of 1.0 (01.0)  0.0%
A:   1.1 (01.1) of 1.0 (01.0)  0.0%
A:   1.1 (01.1) of 1.0 (01.0)  0.0%
A:   1.2 (01.1) of 1.0 (01.0)  0.0%
A:   1.2 (01.1) of 1.0 (01.0)  0.0%
A:   1.2 (01.2) of 1.0 (01.0)  0.0%
A:   1.3 (01.2) of 1.0 (01.0)  0.0%
A:   1.3 (01.2) of 1.0 (01.0)  0.0%
A:   1.3 (01.3) of 1.0 (01.0)  0.0%
A:   1.4 (01.3) of 1.0 (01.0)  0.0%
A:   1.4 (01.3) of 1.0 (01.0)  0.0%
A:   1.4 (01.4) of 1.0 (01.0)  0.0%
A:   1.4 (01.4) of 1.0 (01.0)  0.0%
A:   1.5 (01.4) of 1.0 (01.0)  0.0%
A:   1.5 (01.4) of 1.0 (01.0)  0.0%
A:   1.5 (01.5) of 1.0 (01.0)  0.0%


Exiting... (End of file)


```

---

### Post by GraysonPeddie on 2011-07-02
[SIZE="4"]Solution:[/SIZE]

Do "crontab -e" and add " > /dev/null" at the end of the command, like this:

```
0 * * * * /fileserver/shell_scripts/saytime_hour > /dev/null
```

[size=3]So what happened?[/size]

Cron sends e-mail every hour that I specified, which I don't want it to happen because I don't NEED an output produced from sox/mplayer, so I think it's not only mplayer, but perhaps sox, too.

So that is what's going on. Pardon me for starting such a thread.

---

