---
title: "MKV Mayhem"
date: 2006-03-29
forum: General Help
---

### Post by souteneur3190 on 2006-03-29
Mplayer doesnt seem to play mkv files that great.  I remember one time, i count go forward while watching a movie because it would freeze.  And now the sonund is all distorted.  Like in slow mo.  Does anyone have a better codec?

---

### Post by souteneur3190 on 2006-03-29
or do i need to use some type of setting?

---

### Post by DOtSlaSHuCantCME on 2006-03-29
[QUOTE=souteneur3190]or do i need to use some type of setting?[/QUOTE]

Dont have an answer (yet)to your post,but ive been trying to play this mkv file
and could not,but after  reading ya post it moved me to install  mplayer,and it played the mkv file perfectly.I installed mplayer-586 and mplayer fonts.

EDIT:MY MPLAYER VIDEO SETTINGS=enable double buffering =checked
                                                =enable direct rendering=unchecked
                                                =enable frame dropping =checked
                                                =enable HARD frame dropping =checked
                                                = flip image upside down=unchecked


An alternativei noticed that many people are complaining about not playing mkv files on ubuntu, including myself.....

so i started to compile VLC and noticed that when it's setting the matroska driver it searches for something else...

Before you can play MKV files you need to do the following: In Konsole type...

1- sudo apt-get install libebml-dev

2- sudo apt-get install libmatroska-dev

3- sudo apt-get install libmp4v2-0 libmp4v2-dev

After Installing these 3 files you will need to compile VLC, remember to get all VLC dependencys.. try this

4- sudo apt-get install libdvdcss2 libdvdcss2-dev libdvdplay0 libdvdplay0-dev libdvdnav-dev libdvdnav4 libdvdread3-dev libdvdread3 libogg-dev libogg0 libvorbis-dev libvorbis0a liba52-0.7.4-dev liba52-0.7.4 libmad0-dev libmad0

5- Go to [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)
and download the latest vlc source code, i have 0.8.4a and get ready to compile it...

6- Extract the file typing "tar -zxvf vlc-XXXX.tar.gz" and go in the extraxted directory,

7- Type "sudo ./configure --enable-mkv" (this might take a while)

8- Type "sudo make" (this also might take a while)

9-Type "sudo make install"

if everything went well, try "vlc --list |grep mkv" it should display a line with "mkv Matroska stream demuxer"

i'm assuming that you have installed the packages to compile... if not, try
"sudo apt-get install build-essential autoconf automake1.9"

the above is from this post= [http://www.ubuntuforums.org/showthread.php?t=127563&highlight=playing+mkv+files](http://www.ubuntuforums.org/showthread.php?t=127563&highlight=playing+mkv+files)

---

