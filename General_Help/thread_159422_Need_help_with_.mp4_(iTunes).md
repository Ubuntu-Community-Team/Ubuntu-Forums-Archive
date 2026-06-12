---
title: "Need help with .mp4 (iTunes)"
date: 2006-04-12
forum: General Help
---

### Post by cooldudejz on 2006-04-12
i have downloaded every codec possible, every gstreamer possible and have followed every guide possible to try and get this thing to play, but nothing can play it. mplayer says "cannot find codec for audio format 0x736D7264. does anybody know what i am doing wrong. and if ubuntu just wont play it is there a way i can convert the .mp4 into a .mp3. thanx

---

### Post by truNWA on 2006-04-12
ummm i might be wrong, but i thought mp4's were usually video files, so i don't think you can do that..... but also i don't use a lot of music files


edit:

I think i remember that Itunes puts it's encoded music in mp4 format, so if it's music bought from the store, you can't use it.

---

### Post by castusalbuscor on 2006-04-12
I have the same problem, and I didnt buy the music, I just converted it so that it transfers faster to my iPod.
I managed to play the songs in VLC, but it gets tediius after a while... a music player with a library would be great... any ideas?

---

### Post by souki on 2006-04-12
ffmpeg -i input.mp4 output.mp3

---

### Post by castusalbuscor on 2006-04-12
[QUOTE=souki]ffmpeg -i input.mp4 output.mp3[/QUOTE]


ok... How do I work this then?
Do I type it in the terminal?
Do I have to use su/sudo?

---

### Post by souki on 2006-04-12
[QUOTE=castusalbuscor]ok... How do I work this then?
Do I type it in the terminal?
Do I have to use su/sudo?[/QUOTE]

open a terminal, go to the folder where the mp4 is
then, type this command
```
ffmpeg -i yourfile.mp4 converted.mp3
```
of course, you have to replace yourfile.mp4

---

### Post by JoeMetal on 2006-04-13
If these are music files made with iTunes, they are .m4a not .mp4.  So ffmpeg will not help in this situation.

---

### Post by RikoW on 2006-04-13
If those are m4p files purchased from itunes, they are DRM protected, so you will not be able to play them under Linux, I believe.
If they are bought with sharpmusique from the ITMS, they don't have the DRM added   (and have suffix .m4a) and you can convert them to .wav using faad and then the .wav to .mp3 using lame, for example.

```
faad -o song.wav song.m4a
lame -h -b 192 song.wav song.mp3
```

What do I do with my itunes bought music: I burn them on CD using iTunes and rip the CD under linux. Probably not the 'way of beauty' but works for me, plus I get all the mp3 tags set properly :)

Cheers,

             Riko

---

### Post by qyot27 on 2006-04-13
[QUOTE=JoeMetal]If these are music files made with iTunes, they are .m4a not .mp4.  So ffmpeg will not help in this situation.[/QUOTE]
.m4a and .mp4 are the same thing, there's no difference.  Apple just made up the .m4a extension out of thin air to represent audio files.  Structurally and container-wise, they're the same.  If it won't accept .m4a, just rename them.

There's an MP4/AAC plugin for XMMS.  I just can't remember at the moment where I found it or if you'd need to use alien to convert it to a deb.  But it works very well.

Scratch that: I think it's in the repositories (unfortunately I can't check because I can no longer boot the Ubuntu side of my computer).  Just look for xmms-plugin-mp4.

If it's not in the repos, you can find the .rpm here, which you will then need to convert to deb with alien or alternately, compile from source:
[http://www.qwirx.com/xmms-plugin-mp4/](http://www.qwirx.com/xmms-plugin-mp4/)

---

