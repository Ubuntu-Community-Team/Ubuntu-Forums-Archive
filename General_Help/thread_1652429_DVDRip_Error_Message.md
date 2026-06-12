---
title: "DVD::Rip Error Message"
date: 2010-12-24
forum: General Help
---

### Post by jereece on 2010-12-24
Anyone have an idea why my DVD::Rip fails when I go to transcode it?  I have taken several family movies today and have been successful riping and trasncoding them to AVI except for one. This one riped just fine but when I go to transcode to AVI, I get the following error message.

----------------------------------  

Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/jim/dvdrip-data/Christmas/tmp' && cd /home/jim/dvdrip-data/Christmas/tmp && mkdir -p /home/jim/dvdrip-data/Christmas/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/jim\/dvdrip\-data\/Christmas\/vob\/001\/ -w 8696,50 -b 128,0,2 -s 1.000 --a52_drc_off -f 30,4 -M 2 -X 0,36,8 -R 1 -y xvid,null --psu_mode --nav_seek /home/jim/dvdrip-data/Christmas/tmp/Christmas-001-nav.log --no_split  -o /dev/null --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK

Output: transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.

---

### Post by jereece on 2010-12-25
Never mind.  No offence to Linux but I rebooted into Windows, downloaded a free DVD rip/convert program and in a few minutes had it done.  

Even though I have used Linux for a couple years, I still find software designed for Linux not as user friendly as Windows software.  Too many Linux programs has to be tweaked to get them to work.  In Ubuntu 10,10, I still have printing problems, can't play Blu-ray movies, problems with Osmo, frustrating limitations with Open Office, web site compatibility problems Clipboard issues, and home networking problems.  Linux does have it's strong points however in speed and security.  I guess I'll have to continue dual boot for some time to come.

---

