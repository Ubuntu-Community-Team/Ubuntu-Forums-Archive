---
title: "About media player (VLC)"
date: 2006-03-22
forum: General Help
---

### Post by darkarchon on 2006-03-22
hello everyone. i am very new to linux, and registered in this forum just a few days ago. but it's provided tremendous help for me in understanding how things work, solving problems, installing and configuring stuff, etc...  thank u!
i've noticed that there are many threads in this forum about people trying to find a good media player that would play all of their video files. and it seems that each player works better in some cases and worse or not at all in others.
i've tried about 5-6 different players and got the same impression of not being able to use one single player for all files.
the biggest problem is usually H.264 encoded files, because they really require every bit of your cpu power. the only player that worked for these files for me was MPlayer, but it doesnt adjust the picture size in fullscreen for some reason. the only other player that could playback H.264 files was VLC, that the playback was very slow with many frame drops (especially in my favorite Q3 vid with 50fps frame rate).
so i decided to compile my own version of VLC just to see if it makes things better. as u know, compiling VLC isnt very easy task, especially for linux newbie. so i found .deb package that someone else compiled, and it works astonishingly better than the one in repositories. here it is:
[http://www.niksula.hut.fi/~alaisi/ubuntu/vlc-with-vc1.deb](http://www.niksula.hut.fi/~alaisi/ubuntu/vlc-with-vc1.deb)

now, after installing this package, VLC works great, the way it worked for me back in windows.
my first post, but i hope it solves a lot of troubles for many new users here.

---

### Post by Hairy_Palms on 2006-03-22
ya know if you just start mplayer with the -zoom option then itll resize perfectly.

---

### Post by az on 2006-03-22
[QUOTE=darkarchon]
now, after installing this package, VLC works great, the way it worked for me back in windows.
my first post, but i hope it solves a lot of troubles for many new users here.[/QUOTE]
If you can find details about how it is patched, would you please file a bug report to request this feature in the version in the Ubutnu repositories?  They can even ask for things upstream.

[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by darkarchon on 2006-03-22
first, its good to know that MPlayer can playback fullscreen normally as well, but using a command line option for that is a bit weird, imho it should behave like that by default.
i really dont know how this package was compiled, but it may have been compiled with another version of ffmpeg plugin, which can explain the difference in video playback speed.  where do i submit this 'bug' report? :)

---

