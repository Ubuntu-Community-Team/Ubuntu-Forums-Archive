---
title: "Can't listen to CD's anymore"
date: 2006-06-01
forum: General Help
---

### Post by David of Broadway on 2006-06-01
I just upgraded from Breezy to Dapper and I can't listen to CD's anymore.

I pop in the CD and Sound Juicer opens up and gives the track titles, but when it tries to play them, it gives the error message "Error playing CD / Reason: Could not get/set settings from/on resource" twice, followed by "Error playing CD / Reason: Internal data flow error."  For each subsequent track, it gives the second error message, then the first error message twice, then the second error message again.

Rhythmbox acts similarly, except it doesn't bother to display the error messages.

I have two CD drives, a LITE-ON LTD-52246S and a Sony DVD-RW DRU-800A.  This happens in both drives.

I can read data CD's on both drives (I haven't tried DVD's yet, nor have I tried burning) and everything worked fine in Breezy.  It's not a generic sound card problem; I'm getting sounds elsewhere.

Any ideas?

Thanks.

---

### Post by Bloch on 2006-06-01
Since no-one else has answered, I will, though my knowledge is limited:

There is usually an audio cable connecting the cd output directly to the sound card. If an audio disk is inserted it is recognised and the signal is read directly. Many computers have a cd-out connection on the cd-drive itself - this also outputs music directy from an audio cd.

On my computer - and possibly yours - that cable is missing. I got similar unhelpful error messages. Check to see if you can use Sound Juicer to rip an audio cd. 

If you think it is the missing audio cable (and it is omitted in many brand new computers) then you will need to adjust your players settings so that it reads the cd through the data connection. (This takes a tiny bit more of CPU power, but not noticable on modern systems) I am not in front of my ubuntu box, so can't give you immediate help on that score. I believe amarok plays them through the data cable by default

---

### Post by Slim Odds on 2006-06-01
[quote=Bloch]
There is usually an audio cable connecting the cd output directly to the sound card. If an audio disk is inserted it is recognised and the signal is read directly. Many computers have a cd-out connection on the cd-drive itself - this also outputs music directy from an audio cd.

On my computer - and possibly yours - that cable is missing. I got similar unhelpful error messages. Check to see if you can use Sound Juicer to rip an audio cd. 

If you think it is the missing audio cable (and it is omitted in many brand new computers) then you will need to adjust your players settings so that it reads the cd through the data connection. (This takes a tiny bit more of CPU power, but not noticable on modern systems) I am not in front of my ubuntu box, so can't give you immediate help on that score. I believe amarok plays them through the data cable by default[/quote] 
That's a nice try, but there is no way for software to know about that cable. The only way you can tell if that cable is missing is no sound when playing CD's in analog mode. And, if you are playing audio CD's, you really want to play in analog mode. Otherwise, you're just wasting CPU and I/O bandwidth (especially on older, slower machines).

---

### Post by David of Broadway on 2006-06-03
[QUOTE=Bloch]Since no-one else has answered, I will, though my knowledge is limited:

There is usually an audio cable connecting the cd output directly to the sound card. If an audio disk is inserted it is recognised and the signal is read directly. Many computers have a cd-out connection on the cd-drive itself - this also outputs music directy from an audio cd.

On my computer - and possibly yours - that cable is missing. I got similar unhelpful error messages. Check to see if you can use Sound Juicer to rip an audio cd. 

If you think it is the missing audio cable (and it is omitted in many brand new computers) then you will need to adjust your players settings so that it reads the cd through the data connection. (This takes a tiny bit more of CPU power, but not noticable on modern systems) I am not in front of my ubuntu box, so can't give you immediate help on that score. I believe amarok plays them through the data cable by default[/QUOTE]

Thanks for the suggestion, but I don't think that's the problem.  Playing CD's worked fine before I upgraded from Breezy, and I haven't touched the hardware.  In Breezy, I could play CD's on either drive; in Dapper, I get the same error message from both.

---

### Post by David of Broadway on 2006-06-04
Incidentally, while Sound Juicer can't play the CD, it has no trouble extracting the tracks.

And, more surprisingly, Beep Media Player can play straight off the CD!  It works when set to either analog or digital, although analog is too quiet.  Can Beep be docked?  That's what I liked about Rhythmbox.

---

### Post by Yikes777 on 2006-07-13
I had the same problem. I insalled the "gstreamer-alsa" package and that took care of it.

---

### Post by ddonky on 2006-07-15
I get the error you described when I try to play audio cds or cdrs, and when I try to open them with Totem, I get this error:

'error accessing 'cdda:///dev/hdc': Invalid URI'

DVDs and DVDRs play fine in this drive. 

tail | dmesg returns a bunch of lines of this:

cdrom: This disc doesn't have any tracks I recognize!

BTW, I already have gstreamer-alsa package installed.

---

### Post by ddonky on 2006-07-24
bump

---

### Post by ddonky on 2006-09-27
bump

---

### Post by H.E. Pennypacker on 2006-11-23
> **ddonky said:**
> I get the error you described when I try to play audio cds or cdrs, and when I try to open them with Totem, I get this error:

'error accessing 'cdda:///dev/hdc': Invalid URI'

DVDs and DVDRs play fine in this drive. 

tail | dmesg returns a bunch of lines of this:

cdrom: This disc doesn't have any tracks I recognize!

BTW, I already have gstreamer-alsa package installed.

I am getting the same error with an audio CD.

---

