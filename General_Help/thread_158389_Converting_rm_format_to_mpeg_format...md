---
title: "Converting rm format to mpeg format.."
date: 2006-04-11
forum: General Help
---

### Post by sands on 2006-04-11
can we convert video from one format to another by using Mplayer?
Or is there any other tool to do this??

---

### Post by frodon on 2006-04-11
Maybe kino can do it, it's in the repositories i think : [http://www.kinodv.org/article/static/2](http://www.kinodv.org/article/static/2)

---

### Post by kingmonkey on 2006-04-11
Converting from one media format to another is a bad idea due to serious quality loss.

---

### Post by adamkane on 2006-04-11
Converting from RealVideo is worthy if not rewarding.

---

### Post by adamkane on 2006-04-11
Conversion to AVI is easier than conversion to MPG due to issues with ffmpeg. If you decide to follow these instructions, please post any errors you receive.

RealVideo -> AVI:
[http://priyadi.net/archives/2005/07/30/converting-video-files-to-3gp-for-use-in-cell-phones/]("http://priyadi.net/archives/2005/07/30/converting-video-files-to-3gp-for-use-in-cell-phones/")

Open a terminal:

```

cd path_containing_file_to_convert
mencoder file_to_convert.rm -oac pcm -ovc lavc -lavcopts vcodec=mjpeg -sws 2 -vf scale=176:144 -o output_file.avi -font ~/.mplayer/subfont.ttf -subfont-text-scale 4 -subfont-blur 2 -subfont-outline 1

``` 
You're done, if all you need is an AVI file. 

Continue, if you need an mpeg file. There is no way to create an mpeg directly from a RealVideo file. AVI is the WAV of the video world. Everything gets converted to AVI, before it gets converted to something else.

AVI -> MPEG:
[http://www.ubuntuforums.org/showthread.php?t=62625]("http://www.ubuntuforums.org/showthread.php?t=62625")
[http://www.ubuntuforums.org/showthread.php?t=108255]("http://www.ubuntuforums.org/showthread.php?t=108255")
[http://www.ubuntuforums.org/showthread.php?t=114946]("http://www.ubuntuforums.org/showthread.php?t=114946")

Install ffmpeg (the hard way):
(I put this here in case I need to refer to it later)

```

sudo apt-get install vobcopy cpdvd ogmtools build-essential make checkinstall fakeroot faad gstreamer0.8-faad libfame-0.9 liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-dev libfaad2-0 libdts-dev libogg-dev libvorbis-dev libtheora-dev libgsmme-dev libgsm1-dev libdc1394-13-dev
cd ~
mkdir ffmpeg
cd ffmpeg
sudo apt-get source ffmpeg
cd ffmpeg-0.cvs20050918
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis  --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
make
sudo checkinstall
cd ~
sudo rm -r ffmpeg

``` 

Enter the following during checkinstall:

Description: ffmpeg
Name: ffmpeg
Version: 3.01

Install ffmpeg (the easy way):

```

cd ~/Desktop
wget http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb
sudo dpkg -i ffmpeg_0.20060410T134157_i386.deb

``` 
Open a terminal:

```

cd path_containing_file_to_convert
ffmpeg -i file_to_convert.avi -target ntsc-svcd -sameq -aspect 4:3 -y output_file.mpg

``` 
These instructions show you how to create an SVCD compliant mpeg, because I couldn't find out how to create a generic mpeg.

---

