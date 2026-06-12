---
title: "*2MP3 convertors"
date: 2005-02-28
forum: General Help
---

### Post by Toe Knee on 2005-02-28
Hi,
 I got a MP3 player for christmas but have most music in Ogg and FLAC.  For converting Ogg, I use ogg2mp3 but for FLAC I have to go FLAC>Ogg>mp3.  This is a pain in the  [-X. 
Does anyone know of a good all in one script, or Gnome frontend (or anything else for that matter) that will make my life easier?

Cheers.

---

### Post by Ste on 2005-02-28
[QUOTE=Toe Knee]Hi,
 I got a MP3 player for christmas but have most music in Ogg and FLAC.  For converting Ogg, I use ogg2mp3 but for FLAC I have to go FLAC>Ogg>mp3.  This is a pain in the  [-X. 
Does anyone know of a good all in one script, or Gnome frontend (or anything else for that matter) that will make my life easier?

Cheers.[/QUOTE]
 [http://freshmeat.net/projects/gnormalize/?branch_id=55977&release_id=188341](http://freshmeat.net/projects/gnormalize/?branch_id=55977&release_id=188341)

Gonna use this soon.
If you use it let me know how you get on.

---

### Post by Toe Knee on 2005-03-05
Cheers,

It's mostly good.  Only problem is it's passing -f to flac and flac isn't liking it.  Oh well, I'll have a quick look and see if I can sort it out.

Thanks again.

---

### Post by bored2k on 2005-03-05
[QUOTE=Toe Knee]Cheers,

It's mostly good.  Only problem is it's passing -f to flac and flac isn't liking it.  Oh well, I'll have a quick look and see if I can sort it out.

Thanks again.[/QUOTE]
 [http://mamchenkov.net/blog/item/converting_flac_to_mp3_on_linux](http://mamchenkov.net/blog/item/converting_flac_to_mp3_on_linux)

u ill need to 
> $sudo apt-get install flac lame

---

### Post by Toe Knee on 2005-03-05
Yep, they are.  the problem is [I]/usr/bin/flac -d "/home/toeknee/Desktop/03 - Reason Is Treason.flac" -f -o "/home/toeknee/Desktop/03 - Reason Is Treason.wav"
/usr/bin/flac: invalid option -- f[/I] 
All I do is copy the line to a command line and re-run it minus the -f.  I'm going to loock at the source for gnormalize and remove the -f from the flac command.  That is the problem.  I't isn't not having everyhting installed.

---

### Post by bored2k on 2005-03-05
[QUOTE=Toe Knee]Yep, they are.  the problem is [I]/usr/bin/flac -d "/home/toeknee/Desktop/03 - Reason Is Treason.flac" -f -o "/home/toeknee/Desktop/03 - Reason Is Treason.wav"
/usr/bin/flac: invalid option -- f[/I] 
All I do is copy the line to a command line and re-run it minus the -f.  I'm going to loock at the source for gnormalize and remove the -f from the flac command.  That is the problem.  I't isn't not having everyhting installed.[/QUOTE]
 whats the problem with the -f ?  [ i know zip about sound editing , i just do videos]

---

### Post by Toe Knee on 2005-03-05
I'm not sure, flac just doesn't seem to want the -f option that gnormalize wants to give it.

Taking that out makes it work.

---

