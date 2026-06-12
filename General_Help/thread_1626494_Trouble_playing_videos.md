---
title: "Trouble playing videos"
date: 2010-11-20
forum: General Help
---

### Post by Brii on 2010-11-20
AVI movie files aren't playing well in Ubuntu. I get audio but the screen stays black, there's no picture. i downloaded VLC player and mplayer and neither of them work. Same thing: Black screen with audio.

Is there a codec pack out there that I should download or something?

---

### Post by TeoBigusGeekus on 2010-11-20
Have you installed the restricted extras?

---

### Post by coffeecat on 2010-11-20
VLC comes with its own dependencies. Sounds more like a faulty AVI file than a codec problem. Right-click on one of your problem AVIs > Properties > Audio/Video tab. What codecs (if any) are showing under Video and Audio?

---

### Post by Brii on 2010-11-20
> **coffeecat said:**
> VLC comes with its own dependencies. Sounds more like a faulty AVI file than a codec problem. Right-click on one of your problem AVIs > Properties > Audio/Video tab. What codecs (if any) are showing under Video and Audio?

Every file and even other video playing programs do the same thing so i think it has something to do with the system

I attached a picture of the properties window.

---

### Post by karthick87 on 2010-11-20
Try this then, install mplayer-nogui and play your videos from terminal.

```
sudo aptitude -y install mplayer-nogui
```Playing video from terminal:

    ```
mplayer /path/to/your/video/file
```Almost all the video's can play here.None of the video's failed for me.

---

### Post by coffeecat on 2010-11-20
Hmm. Xvid and mp3 shouldn't be a problem. When I said that VLC came with its own dependencies I was sure that it didn't need the restricted-extras stuff, but try installing the package ubuntu-restricted-extras (if you haven't already) just in case.

---

### Post by Brii on 2010-11-20
> **coffeecat said:**
> Hmm. Xvid and mp3 shouldn't be a problem. When I said that VLC came with its own dependencies I was sure that it didn't need the restricted-extras stuff, but try installing the package ubuntu-restricted-extras (if you haven't already) just in case.

Installed them, but still nothing...

---

### Post by karthick87 on 2010-11-20
> **Brii said:**
> Installed them, but still nothing...


Have you tried the one which i told you in my last post.

---

### Post by Brii on 2010-11-20
> **karthick87 said:**
> Have you tried the one which i told you in my last post.

Yeah I tried and got this error:

mplayer: relocation error: mplayer: symbol rgb24toyv12, version LIBSWSCALE_0 not defined in file libswscale.so.0 with link time reference

---

### Post by SeijiSensei on 2010-11-20
I've rarely had problems with AVI, particularly if the files are encoded with XviD.

Might I suggest trying the version of mplayer that is maintained by the developer of the excellent smplayer GUI?  Follow the instructions on [this page](https://launchpad.net/~rvm/+archive/ppa) to add the repository.  (Launchpad seems rather slow at the moment, so be patient.)

Otherwise you might try compiling your own copy of mplayer to see if that will do the trick.  See

[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)
[http://ubuntuforums.org/showpost.php?p=10106966&postcount=10](http://ubuntuforums.org/showpost.php?p=10106966&postcount=10)

---

### Post by TeoBigusGeekus on 2010-11-20
Another option for you is to try and convert it to a normal avi using ffmpeg:
```
ffmpeg -i filename.avi -vtag xvid -vcodec mpeg4 -acodec libmp3lame -b 2000k -ab 192k filename1.avi
```

---

### Post by Brii on 2010-11-21
> **TeoBigusGeekus said:**
> Another option for you is to try and convert it to a normal avi using ffmpeg:
```
ffmpeg -i filename.avi -vtag xvid -vcodec mpeg4 -acodec libmp3lame -b 2000k -ab 192k filename1.avi
```

I wouldn't want to do that for ever video.

I think somethings wrong with the Operating System or something. Anyone got any ideas?

---

### Post by toll on 2012-04-19
Somehow but superuser`s apt-get install ffmpeg helped. :popcorn:

---

### Post by coffeecat on 2012-04-19
Old thread - closed.

---

