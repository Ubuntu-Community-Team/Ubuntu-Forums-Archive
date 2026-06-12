---
title: "avi to psp converter installation problem"
date: 2010-03-29
forum: General Help
---

### Post by samenkov on 2010-03-29
Hi,
I'm pretty new to Linux and i've been trying to install a avi (and others) to psp converter.
I started that installation but got an error message half-way through.
[http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml](http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml)

This is the error message:

#####################################
Configure Started
#####################################
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
EXTRA Cflags:
EXTRA CXXflags:
-- <Checking for Subversion>
-- <***********************>
-- Getting svn version from /home/sam/avidemux_2.4_branch
-- Current revision is 6028
-- <Checking for PKG-CONFIG>
-- <***********************>
-- OK /usr/bin/pkg-config
-- <Checking for LibXML2>
-- <*********************>
CMake Error at CMakeLists.txt:74 (MESSAGE):
  Could not find Libxml2


-- Configuring incomplete, errors occurred!

-----------------------------------------------------------------------

I also didn't find the "Add/Remove Programs" under Applications, so i couldn't do the changes in [B]ubuntu restricted extras.

[/B]Can someone help me?

Thanks a lot!

---

### Post by kokkus on 2010-03-29
Ok so this is a windows program you are running trhough Wine, right? There are many better solutions for ubuntu. Converting video using a windows application can mess up the video and its key frames.

Here's what I do, and now I can convert all video formatss with a simple command.


Open up synaptic and ensure that you have ffmpeg and ruby installed/
apt-get install ruby ffmpeg liblame-dev libxvidcore4-dev libx264-dev libfaac-dev libfaad2-dev
sudo apt-get build-dep ffmpeg
Download the script:



Code:

--------------------------------------------------------------------------------

wget [http://thomer.com/howtos/mp4ize](http://thomer.com/howtos/mp4ize)

--------------------------------------------------------------------------------
 
Make it so you can run it:


Code:

--------------------------------------------------------------------------------

chmod +x mp4ize

--------------------------------------------------------------------------------
 
Move it so it's system-wide:


Code:

--------------------------------------------------------------------------------

sudo mv mp4ize /usr/local/bin

--------------------------------------------------------------------------------
 
Now, if you want to convert a video, just open up a terminal and type mp4ize [videoname] and it will make an IPod mp4 version in the same folder. Enterprising Nautilus Actions users may want to add a right click menu version for this by adding /usr/local/bin/mp4ize as a path and %M as a parameter.

If everything goes well, your output will look like this:
[email]root@ion:/extra/movies/Life.Support.DVDRip.XviD[/email]-BeStDivX/Sample# ls
bestdivx-lifes-sample.avi
[email]root@ion:/extra/movies/Life.Support.DVDRip.XviD[/email]-BeStDivX/Sample# mp4ize bestdivx-lifes-sample.avi 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-libgsm --enable-x264 --enable-a52 --extra-cflags=-Wall -g -fPIC -DPIC 
libavutil version: 49.0.0
libavcodec version: 51.11.0
libavformat version: 50.5.0
built on Nov 3 2006 21:14:27, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, avi, from 'bestdivx-lifes-sample.avi':
Duration: 00:01:00.0, start: 0.000000, bitrate: 1071 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 576x320, 23.98 fps(r)
Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Must supply at least one output file
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-libgsm --enable-x264 --enable-a52 --extra-cflags=-Wall -g -fPIC -DPIC 
libavutil version: 49.0.0
libavcodec version: 51.11.0
libavformat version: 50.5.0
built on Nov 3 2006 21:14:27, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, avi, from 'bestdivx-lifes-sample.avi':
Duration: 00:01:00.0, start: 0.000000, bitrate: 1071 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 576x320, 23.98 fps(r)
Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Output #0, mp4, to 'bestdivx-lifes-sample.mp4':
Stream #0.0: Video: xvid, yuv420p, 320x240, q=3-5, 400 kb/s, 23.98 fps(c)
Stream #0.1: Audio: aac, 48000 Hz, stereo, 128 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 1439 q=3.0 Lsize= 3734kB time=59.9 bitrate= 510.6kbits/s 
video:2763kB audio:936kB global headers:0kB muxing overhead 0.928542%
[email]root@ion:/extra/movies/Life.Support.DVDRip.XviD[/email]-BeStDivX/Sample# ls
bestdivx-lifes-sample.avi bestdivx-lifes-sample.mp4
[email]root@ion:/extra/movies/Life.Support.DVDRip.XviD[/email]-BeStDivX/Sample#


You can also use Avidemux if this solution was too complicated to you

---

