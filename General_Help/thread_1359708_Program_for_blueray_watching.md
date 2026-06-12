---
title: "Program for blueray watching"
date: 2009-12-20
forum: General Help
---

### Post by Nick01 on 2009-12-20
Does anybody know with what program can i watch high def/blueray movies?

Thank you

---

### Post by Treeh on 2009-12-20
There isn't one really...although you could try this: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I recommend a Windows partition, or if your computer is powerful enough, using a virtual machine (or WINE, if it works...).

---

### Post by DeMus on 2009-12-20
I'm also looking for this and did find a media centre which can play the individual Blu-Ray disc files, but not the complete thing.
It means you have to go down the tree to the folder where all the m2ts files are located, look for the largest file and open it with the program. You can choose all sorts of settings regarding audio, video and subtitles, but it's still not the complete Blu-Ray.
I'm talking about xbmc which you can get at: [_XBMC_]("http://xbmc.org")

---

### Post by Treeh on 2009-12-20
> **DeMus said:**
> I'm also looking for this and did find a media centre which can play the individual Blu-Ray disc files, but not the complete thing.
It means you have to go down the tree to the folder where all the m2ts files are located, look for the largest file and open it with the program. You can choose all sorts of settings regarding audio, video and subtitles, but it's still not the complete Blu-Ray.
I'm talking about xbmc which you can get at: [_XBMC_]("http://xbmc.org")

Out of curiosity, how does that work with the encryption?

---

### Post by DeMus on 2009-12-20
> **Treeh said:**
> Out of curiosity, how does that work with the encryption?

I installed the W32 and W64 codecs, ubuntu-restricted-extras, ffmpeg and probably some more and it works great. I can also watch the same files in VLC, but without the subtitles (if you should need them).

---

### Post by 3rdalbum on 2009-12-20
> **Treeh said:**
> Out of curiosity, how does that work with the encryption?

I believe you have to decrypt them first... or it might run dumphd and pipe the output to Mplayer. Either way, it's not licensed.

---

### Post by pedja_portugalac on 2009-12-20
> **DeMus said:**
> I installed the W32 and W64 codecs, ubuntu-restricted-extras, ffmpeg and probably some more and it works great. I can also watch the same files in VLC, but without the subtitles (if you should need them).

How can you install w32 and w64 on same machine? vlc can NOT handle blue rays nowadays, even decrypted ones... The only way to watch those kind of movies on linux is decrypting them on first place using program for windows called anydvd or dumphd on linux and then using svn-mplayer to play back the largest file, that's main movie.

---

### Post by DeMus on 2009-12-20
> **pedja_portugalac said:**
>  vlc can NOT handle blue rays nowadays, even decrypted ones... The only way to watch those kind of movies on linux is decrypting them on first place using program for windows called anydvd or dumphd on linux and then using svn-mplayer to play back the largest file, that's main movie.

Well excuse me, but in the last couple of weeks I am watching one Blu Ray after another and I did it with VLC. Now I installed the XBMC media centre and I can even switch on the subtitles.
I open Nautilus and dive into the BluRay folders until I see the folder Stream which contains the video files. I look for the largest file and open it with VLC (now with XBMC) and that's it.

---

### Post by 3rdalbum on 2009-12-20
> **pedja_portugalac said:**
> How can you install w32 and w64 on same machine? vlc can NOT handle blue rays nowadays, even decrypted ones... The only way to watch those kind of movies on linux is decrypting them on first place using program for windows called anydvd or dumphd on linux and then using svn-mplayer to play back the largest file, that's main movie.

MakeMKV is another solution for extracting Blu-rays, and depending on the disc you can usually just use the regular Mplayer that you get for Ubuntu.

---

### Post by pedja_portugalac on 2010-01-02
> **DeMus said:**
> Well excuse me, but in the last couple of weeks I am watching one Blu Ray after another and I did it with VLC. Now I installed the XBMC media centre and I can even switch on the subtitles.
I open Nautilus and dive into the BluRay folders until I see the folder Stream which contains the video files. I look for the largest file and open it with VLC (now with XBMC) and that's it.
Unbelievable, you mean without decryption? I can't believe that.
> **3rdalbum said:**
> MakeMKV is another solution for extracting Blu-rays, and depending on the disc you can usually just use the regular Mplayer that you get for Ubuntu.
makemkv can't decrypt all BD. Actually, it wasn't able to decrypt single one I've tried to decrypt with it. The only one who was able to decrypt every BD I had was anydvd.

---

### Post by rhinert on 2010-01-03
> **DeMus said:**
> ....in the last couple of weeks I am watching one Blu Ray after another and I did it with VLC. Now I installed the XBMC media centre and I can even switch on the subtitles.




I've got the XBMC media center installed and I put a dvd in the drive.  Even tho the DVD in the drive is mounted in USB automounter, I get no menu options for the drive or USB inside the media center.  It does give me the option of manually inputting a source for video.

I checked under the root file system under /mnt and /media but the dvd drive is not mounted there.  Any ideas of a mount point for this drive??  I'm running 9.1 kubuntu.

---

