---
title: "an avi/wmv converter for ubuntu???"
date: 2006-05-29
forum: General Help
---

### Post by darkstrikera2 on 2006-05-29
does anyone know where i can find one? i searched and dont seem to have any luck. ive heard mplayer can play wmvs and avis, but i can install that. I am currently using VLC. if there are any codecs that allow VLC to play those audio types, please let me know.

---

### Post by nalmeth on 2006-05-29
YOu have to install the restricted codecs. If you're on dapper (the new release) here's a link for the bump's multimedia script. [http://www.ubuntuforums.org/showthread.php?t=138889]("http://www.ubuntuforums.org/showthread.php?t=138889")

Automatix is for breezy (old release), see the link in my signature.

If you want a video editing program, try avidemux.

EDIT: sorry, noticed you're in the 5.10 section. That's breezy, if you are sure that's right, use automatix.
Or manually [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by darkstrikera2 on 2006-05-29
no luck, i typed in "[COLOR="Red"]wget [http://beerorkid.com/automatix/automatix_5.8-4_i386.deb](http://beerorkid.com/automatix/automatix_5.8-4_i386.deb)
sudo dpkg -i automatix_5.8-4_i386.deb[/COLOR]" from that link under your sig. and it said it installed it i think, but i tried an wmv file, and it didnt work. :( 

also, my sound does not work for the videos i do play, but it works when i play audio. how do i fix that?

---

### Post by darkstrikera2 on 2006-05-29
and the audio in flash doesnt work either! wtf

---

### Post by nalmeth on 2006-05-29
sorry, you have to run the script, then the script will install the codecs for you, or whatever else you select.

Go to Applications --> System Tool's --> Automatix

I have had some problem's with audio in flash if I am playing video from the HD first. I think there is a thread on this issue, perhaps a solution. Perhap's not. Try CNTL-ALT-BACKSPACE, log back in, and try the flash video first.

---

### Post by darkstrikera2 on 2006-05-29
thank you very much man, you are awesome, im at the part where i install packages( i havnt actually tested it to see if it works)  but do i have to install ALL of the packages, or just the ones i want?

---

### Post by nalmeth on 2006-05-29
No prob.
Just install what you want. There's some good stuff in there, but you probably don't need it all. In fact, considering that Dapper is 3 days from release, you may want to keep it to a minimum to avoid upgrade issues. I've heard that firefox 1.5 causes problem's, but upgrading to dapper will give you firefox 1.5 anyway, so I would hold off on that. Search the forums for other upgrading concern's, if you are concerned..

Have a good one

---

### Post by darkstrikera2 on 2006-05-29
yeah, went ahead and install about 8-10 things that looked good (fortunately firefox 1.5 wasnt one of them, thank you for telling me about that) and its installing the things as we speak.  thanks again for your help.

---

