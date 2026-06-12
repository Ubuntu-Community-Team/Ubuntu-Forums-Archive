---
title: "Subtitles in .mkv files"
date: 2006-01-31
forum: General Help
---

### Post by renzokuken on 2006-01-31
i am having a difficult time getting the subs to appear in my .mkv files

i use mplayer, and the video is fine as is the audio but alas no subs.

i tried totem xine and all i got was audio and in vlc absolutely nothing.

does anyone know how to get the subs working? i tried the file on a Windows machine with XP Codec Pack installed and it works fine so subs are definately present.

edit, just tried xine-ui and same prob.

the codecs i have installed were done through automatix, whereas before i did it by dropping the win32 codec files from the mplayer website into /usr/lib/win32 (i cant remeber whether mkv files worked when i did it this way)

any ideas, thanks

---

### Post by renzokuken on 2006-01-31
ok, sorry for the waste of a thread but i fixed it by running

# mplayer -slang eng videofile.mkv

---

### Post by JackandJohn on 2006-05-05
Definately not a waste since you resolved it: worked like a charm for me :)


P.s. Since this was also an h264/5.1 aac HD video; I realized that there is a significant performance drop if you are downmixing to stereo (if you get stuttering, enable 5.1 if at all possible; even if you don't have 5 channels)

---

### Post by phorque on 2006-05-20
That really does work! Is there any way to find out what audio/subtitle tracks your file has to choose from? I got a message in one of my files that said "If you are seeing this please swith to the second subtitle track" and I have no idea what that would be.

edit: With the gui, there are a bunch of hotkeys for switching subtitles, v enables/disables and j cycles through them.

---

### Post by nami on 2006-05-21
I have an avi and mkv files with external srt sub files.  anyone know how to enable these subs?

---

### Post by diacronic on 2006-06-10
Ok Hate to bring this back up but im having a bit of trouble with it. 
If i run the file using the "mplayer -slang eng" command it plays fine with teh subtitles BUT i have no controls over the video. No pausing no full screen nothing.

SO then I try to edit the config files for it in both /etc and the /home/.mplayer folder either way when i add the slang=en or eng line to it the text gets all messed up and just shows smile faces and otehr nonsense. Maybe i am over looking something. Thanks in advance.

---

### Post by onlysolution on 2006-07-08
> **phorque said:**
> 
edit: With the gui, there are a bunch of hotkeys for switching subtitles, v enables/disables and j cycles through them.

Try starting normally and using those hotkeys to find your subs?  Worked just fine for me that way.

---

### Post by aresgoddess on 2006-09-02
Does anyone know how to fix the subtitles in Totem? Mplayer screws up a lot for me, so I prefer using Totem, but when I play mkv files, the subtitles option is always inactive. Actually, it's that way for Mplayer as well. I know the files work because other people are able to view the subtitles on them. Thanks in advance.

---

