---
title: "How remove errant directory"
date: 2009-10-01
forum: General Help
---

### Post by onespeedbiker on 2009-10-01
Somehow the following dirctory has been palced in the media directory /media/DVD/VIDEO_TS. The directory/ files are for a DVD I burnt. The problem ubuntu now thinks it must use this directory when watching and burning dvd's, instead of the correct media/cdrom directory. Can someone help me get rid of this directory. I have tried sudo -rf /media/DVD/VIDEO_TS

rm: cannot remove `/media/DVD/VIDEO_TS/VIDEO_TS.IFO': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VIDEO_TS.BUP': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_0.IFO': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_1.VOB': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_2.VOB': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_3.VOB': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_4.VOB': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_5.VOB': Read-only file system
rm: cannot remove `/media/DVD/VIDEO_TS/VTS_01_0.BUP': Read-only file system

and get this error. How can I fix this?

---

### Post by scragar on 2009-10-01
The DVD is mounted, you can't delete the files because they are on the DVD.

If that's wrong then run ```
mount
```And see what's mounted there.

---

### Post by onespeedbiker on 2009-10-01
Okay I understand that now; it was on a dvd I had mounted. 

The real problem seems to be what IO believe is the ubuntu scsi emulation has broken down. Previously when I started a video it ran from "cdrom"; now it is running from "DVD". The result is I can not burn any dvds while it's in this mode. The last time it happened I continually tried to burn a dvd until suddenly the /media/ window popped up and it started running in scsi emulation mode again. This happened the last time I had a major update. So far I have been unable to jolt unbuntu back to scsi emulation so my dvd burner is dead. Is there any fix for this?

BTW, the fact that the videos are running "from" "DVD" does not mean I am somehow trying to burn a running dvd. It is simply a symptom or sign, that it is in this mode, where something has broken down preventing ubuntu from accessing the dvd device as a burner.

---

