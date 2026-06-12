---
title: "Playing Music"
date: 2006-03-01
forum: General Help
---

### Post by nikkolas on 2006-03-01
Hi all I installed Dapper Flight 2 on my Acer Laptop.  It is running nice with a few bugs here and there, which I don't mind. For a Beta version the OS is running smooth. My biggest problem is that when I connect my PSP the system detects it as a SDA1 drive.  When I try to access the music files from it I cannot play it in Amarok or any other media player.  I have to use KPSP (or ioslave).  By typing "psp:/" in the file search area in Amarok I can play the music.  Also I try accessing my windows hda drive, with music files on it.  And the same thing happen I cannot play the songs from the windows drive.  Can someone help me out and let me know what I can do to fix this.  Thanks much help is appreciated or any tip. Thanks in advance:D 

Nikk \\:D/

---

### Post by gingermark on 2006-03-01
This is the Breezy forum, but I think it's the same for Breezy.

amaroK struggles to play music from remote media (ie from a location that begins "system:/ " or similar). 

You need to mount the drive at a particular point (use the "Disks & Filesystems" options in System Settings or the Control Centre). To use your Windows drive as an example, I think you'll have trouble playing something from system:/hda but if you mounted it as /media/hda it should play.

Not too sure how that would work for your PSP, I would guess mounting it at /media/sda1 might work, but if you can get it to play anyways, I suppose it isn't that much of an issue.

If you still have problems, posting in the Dapper forum will probably grab the attention of folks who are more familiar with that version.

---

### Post by nikkolas on 2006-03-01
Thanks for your reply.  I will try and see if it works.  If it does thank you and if it doesn't, still I want to thank you for your help.  Sorry for posting it in the wrong forum.  Thanks again

---

