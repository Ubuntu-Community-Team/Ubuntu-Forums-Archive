---
title: "MP3 ripping app with more control over output filename syntax?"
date: 2006-05-16
forum: General Help
---

### Post by illiterate_light on 2006-05-16
I'm running Ubuntu 5.10 and have been looking for an mp3 ripper with one simple feature, which is the ability to control the output filename.  Sound Juicer outputs files the way it wants to with no ability to control it, as does Banshee.  I found K3B, which is basically exactly what I want, except that it's buggy and I have to manually enter the ID3 tags for album (and genre, if I want it) for every single CD I rip.  K3B is designed to do what I want, but doesn't work like it's designed to.

Anyone have any suggestions?  I don't even care if I have to do it by command line -- I just want to be able to rip CDs in mp3 format, and control the output filenames and destination folders -- all I want is everything to appear in ../artist/album/Artist - Album - Track# - TrackName.mp3.

Anyone know of a stable app that will do that, or a way to make K3B work like it should?  Any help appreciated.

---

### Post by RikoW on 2006-05-16
try "grip" which is in the repos.

under the "config"  it lets you configure path and filename for ripping and encoding separately using the tag information from the CDDB, e.g.:

~/MyMusic/mp3/%A/%d/%t_%n.%x

with %A "Artist",  %d "Album Title" (?),   % t "track number",  %n "track title" etc

works very nicely for me! :)
Hope that helps,

               Riko

---

### Post by illiterate_light on 2006-05-16
[QUOTE=RikoW]try "grip" which is in the repos.[/QUOTE]

Oh yeah... I should have mentioned I tried Grip too, but it was unable to recognize my CD drive, after a couple days of troubleshooting and scouring the forums.  Beep and Grip both have the same problem, but every other app I've tried recognizes it fine.  Looks like Grip would also do what I want, but unfortunately it's also useless to me.  Thanks though... if anyone has any other ideas I'd appreciate it.

---

### Post by Stinger on 2006-05-16
Try [ripperX]("http://sourceforge.net/projects/ripperx/") the best CD ripper available for linux IMO :mrgreen: 

Or you could install [EAC]("http://appdb.winehq.org/appview.php?appId=1190") using [Wine]("http://appdb.winehq.org/")

Both works fine here !
8)

---

### Post by illiterate_light on 2006-05-16
[QUOTE=Stinger]Try [ripperX]("http://sourceforge.net/projects/ripperx/") the best CD ripper available for linux IMO :mrgreen: [/QUOTE]

ripperX rules.  That's exactly what I needed, and it's even in the repos.  Problem solved -- thank you.

---

