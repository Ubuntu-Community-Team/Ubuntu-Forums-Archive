---
title: "Help setting up a file server/media center"
date: 2009-11-05
forum: General Help
---

### Post by sabutuga on 2009-11-05
Hi there,

I'm embracing a new project.

I planning on building a file server and media center on one machine.

My base will be a second hand IBM Pentium Duo Core2 2.33ghz motherboard/processor, I'm planning on using 3 HDD (one for software, one for media and one for files that will be split between different users)

Sound and image for the media center will be provided by a TV and a stereo/amplifier.

For software I'm planning on using Ubuntu 9.04, Samba and XBMC (and some other packages like firestarter for safety)

Any advice or help with links to tutorials and how-to's would be greatly appreciated.

Many thanks

---

### Post by thesheff17 on 2009-11-05
I have done this for years and can give you some suggestions.  Always use samba shares for reading/writing for all audio and video.  the smb protocol is very quick.  I'm not sure if you are streaming them over a network but I would also recommend a 1000mbs switch.  They are very cheap these days and so nice for streaming/copying data around on your network. 

 I would also recommend using raid for redundancy.  You can buy a sata raid card with 4 ports and easily run ubuntu 9.04 in RAID5.  I would also recommend using the extra drive as a hot spare and not in the raid array itself.  Then you will have seem less fail over in case anything goes wrong with a drive.  Also buying an extra 1TB drive is always a plus and just run a rsync from your raid array to the drive once a night to ensure you will always have your data.

For playing movies I would def say use vlc.  vlc is one the greatest program for playing dvd's or other format files.  I like XBMC and had it on my xbox but that took a dump and pitched it in the garbage can.  Now I have a stand alone machine with vlc attached to the tv.  Let me know how your setup goes and if you have any other questions.

---

### Post by Giblet5 on 2009-11-05
> **thesheff17 said:**
> RAID5

I was nodding like crazy until that one word.

Use RAID 1/0. The performance is double and it's adequately secure.

Even enterprise users don't use RAID5 now. It's too slow.

---

### Post by sabutuga on 2009-11-06
Thank you for your help thesheff17 and I'll keep your advice in mind as well Giblet5.

This is my first project so it will be very likely that I'll be posting more questions.

---

### Post by thesheff17 on 2009-11-06
Yea I guess I have only built my media servers with 3 drives and that is why I have used raid 5.  Now that drives are so cheap there is no reason to run raid 1/0.

---

### Post by sabutuga on 2009-11-10
Pentium Duo Core2 2.33ghz or Pentium 4?

I'm wondering about power consumption, noise and heat. What should I use as  a cpu?

---

### Post by sabutuga on 2009-11-25
Hi there, one day into starting my project and I have a hardware problem that have been posted here: [http://ubuntuforums.org/showthread.php?t=1336868](http://ubuntuforums.org/showthread.php?t=1336868)  can anyone help?

thanks

---

